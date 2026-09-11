---
title: "Why are users failing the onboarding?"
excerpt: "A Product Analytics case study on identifying, grouping and interpreting the reasons behind onboarding failures."
collection: portfolio
category: "Product Analytics"
header:
  teaser: 
---

# 🔎 Why are users failing the onboarding?

> **Product Analytics Case Study**  
> Funnel Analysis · User Segmentation · Python · Product Strategy

---

## 💡 The Business Question

A fictional fintech app allows users to check their eligibility for a financial product through a short onboarding questionnaire.

Users can enter the questionnaire from two different entry points:

- **Apply Now** — users explicitly interested in starting an application.
- **Check Eligibility** — users who first want to understand whether they meet the requirements.

After completing the questionnaire, users can either:

- successfully pass the eligibility check;
- fail because one or more requirements are not satisfied.

The Product team noticed that a significant number of users were failing the questionnaire.

The initial question was simple:

> **Why are users failing the onboarding?**

However, simply ranking the most frequent failure reasons would not be enough.

I wanted to understand:

1. What are the most common failure reasons?
2. Are users usually failing because of **one problem or multiple problems**?
3. Which problems tend to occur together?
4. Do users coming from different **entry points** experience the same problems?
5. What product actions could potentially reduce avoidable failures?

---

## 🔐 About the Data

This case study is inspired by real-world Product Analytics problems I have worked on.

**All data, product names, business rules and results shown below have been synthetically generated and do not represent any company, customer or production dataset.**

The purpose of this project is to demonstrate the analytical methodology and reasoning process.

---

# 1. Understanding the Data

For this analysis, I generated a synthetic dataset representing **10,000 questionnaire sessions**.

A simplified version of the dataset looks like this:

| user_id | timestamp | entry_point | version | outcome | failure_reason |
|---|---|---|---|---|---|
| 10452 | 2026-08-03 | apply_now | v2 | fail | missing_documents |
| 10453 | 2026-08-03 | check_eligibility | v2 | pass | — |
| 10454 | 2026-08-03 | apply_now | v2 | fail | unsupported_contract,missing_documents |
| 10455 | 2026-08-03 | check_eligibility | v2 | fail | affordability |

One important characteristic of the data immediately changes the analysis:

> **A single failed questionnaire can have multiple failure reasons.**

For example:

```text
unsupported_contract,employment_tenure,missing_documents
```

Therefore, treating `failure_reason` as a standard categorical variable would hide important information.

---

# 2. How Common Is Each Problem?

The first step is to split combinations of failure reasons and calculate how frequently each individual reason occurs.

For example, the following observation:

```text
unsupported_contract,missing_documents
```

contributes to both:

```text
unsupported_contract
missing_documents
```

After exploding the multi-value field, I calculate an **Occurrence Rate**:

> Percentage of failed questionnaires in which a specific problem appears.

The most frequent problems are:

| Failure reason | Occurrence Rate |
|---|---:|
| Missing documents | **46%** |
| Employment tenure | **43%** |
| Unsupported contract | **41%** |
| Affordability | **34%** |
| Income requirement | **22%** |
| Residency requirement | **7%** |

Percentages intentionally **do not sum to 100%**, because the same user can experience multiple problems.

### First Insight

At first glance, documentation and employment-related requirements appear to dominate the failures.

But frequency alone does not tell us whether these are **independent problems**.

---

# 3. Are Users Failing for One Reason or Multiple Reasons?

The next question is therefore:

> **How complex is a typical failure?**

I count the number of distinct failure reasons associated with each questionnaire.

The distribution shows:

| Number of reasons | Share of failed questionnaires |
|---|---:|
| 1 reason | **38%** |
| 2 reasons | **28%** |
| 3 reasons | **16%** |
| 4+ reasons | **18%** |

This means that approximately:

> **62% of failed questionnaires contain at least two different failure reasons.**

### Product Implication

A failure is usually **not caused by a single isolated issue**.

This matters because solving one problem may not necessarily make the user eligible.

For example, helping a user provide a missing document may have limited impact if that same user also has an unsupported employment contract.

---

# 4. Which Problems Occur Together?

To investigate this further, I classify every occurrence of a failure reason as:

- **Alone** — the reason is the only problem detected.
- **With others** — at least one additional problem is present.

The results reveal a very different picture:

| Failure reason | Alone | With other reasons |
|---|---:|---:|
| Missing documents | **0%** | **100%** |
| Unsupported contract | **8%** | **92%** |
| Employment tenure | **18%** | **82%** |
| Affordability | **76%** | **24%** |
| Income requirement | **4%** | **96%** |

This is one of the most important findings of the analysis.

### Employment-related Problems Are Highly Interconnected

The three most frequent reasons:

- Missing documents
- Unsupported contract
- Employment tenure

very frequently appear together.

For example:

> **Every user failing because of missing documents also presents at least one additional problem.**

Similarly, more than 90% of users with an unsupported contract also experience another constraint.

This suggests that these reasons may actually describe different manifestations of the same broader problem.

---

# 5. Moving from Reasons to Macro-Problems

At this point, analyzing individual error codes becomes less useful.

I therefore group them into broader **problem families**.

```text
Employment eligibility
├── Unsupported contract
├── Employment tenure
└── Missing documents

Affordability
├── Affordability
└── Income requirement

Residency
└── Residency requirement

Other
└── Other eligibility constraints
```

This transformation makes the analysis much more actionable.

Instead of asking:

> "How can we reduce `missing_documents`?"

the Product team can ask:

> **"How should we handle users who are currently not eligible because of their employment situation?"**

This is a much more meaningful product question.

---

# 6. Structural vs Recoverable Failures

Not every failure has the same meaning.

Some problems may be **structural**:

```text
Unsupported contract
Residency requirements
Affordability constraints
```

while others may be **temporary or potentially recoverable**:

```text
Missing documents
Employment tenure
Incomplete information
```

This distinction is important.

A user who is permanently ineligible should probably receive a different experience from someone who might become eligible **in a few weeks or after providing additional information**.

Therefore, I would introduce another analytical dimension:

| Problem | Type | Potential Product Action |
|---|---|---|
| Missing documents | Recoverable | Explain required documents |
| Employment tenure | Potentially recoverable | Invite user to return later |
| Unsupported contract | Structural | Explain eligibility constraints |
| Affordability | Potentially actionable | Suggest alternative configuration |
| Residency | Structural | Explain requirements |

The objective changes from simply reducing failures to:

> **Understanding which failed users can realistically be recovered.**

---

# 7. Does the Entry Point Matter?

The product has two ways of entering the same questionnaire.

### Apply Now

A strong-intent CTA for users who want to start the application.

### Check Eligibility

A softer CTA for users who first want to understand whether they qualify.

I therefore segment the failure analysis by entry point.

The results show:

| Failure reason | Apply Now | Check Eligibility |
|---|---:|---:|
| Missing documents | **51%** | **40%** |
| Unsupported contract | **46%** | **31%** |
| Employment tenure | **40%** | **41%** |
| Affordability | **37%** | **47%** |
| Income requirement | **35%** | **20%** |

The difference is substantial.

### Apply Now

Users are more likely to encounter **employment and documentation-related constraints**.

### Check Eligibility

Users are considerably more likely to fail because of **affordability**.

Interestingly, employment tenure remains almost identical across the two populations.

---

# 8. The Product Insight

At this point, the analysis is no longer simply about understanding failure reasons.

The data suggests something more important:

> **Apply Now and Check Eligibility are intercepting users with different needs and different eligibility profiles.**

This raises a product question:

> **Should these users experience exactly the same onboarding flow?**

Probably not.

The entry point itself contains information about **user intent**.

Someone clicking *Apply Now* may benefit from an experience optimized around completing the application and resolving documentation issues.

Someone clicking *Check Eligibility* may instead need more support around affordability, requirements and understanding what options are realistically available.

---

# 9. From Insight to Product Actions

Based on the analysis, I would explore three product opportunities.

### 🔄 Recoverable Failure Journeys

Instead of treating every failure as a dead end, identify users with temporary constraints and create specific recovery journeys.

For example:

```text
Employment tenure too short
        ↓
Explain requirement
        ↓
Estimate eligibility date
        ↓
Reminder / notification
        ↓
Retry questionnaire
```

### 🎯 Entry-Point-Specific Experiences

Use the entry point as a signal of user intent.

```text
Apply Now
→ application-oriented onboarding
→ documentation support
→ recovery actions

Check Eligibility
→ educational onboarding
→ affordability guidance
→ alternative scenarios
```

### 🧩 Macro-Problem Messaging

Instead of displaying multiple technical reasons independently, communicate the **underlying problem**.

For example, rather than:

```text
Missing documents
Employment tenure
Unsupported contract
```

the interface could explain:

> "At the moment, your employment situation does not meet the eligibility requirements."

The detailed reasons can still be provided when useful.

---

# 10. What Would I Test?

The analysis generates hypotheses, but it does not prove that changing the experience will improve conversion.

The next step would therefore be experimentation.

## Experiment 1 — Recoverable Failures

**Control**

```text
Eligibility check failed
```

**Variant**

```text
Eligibility check failed
+
explanation
+
next eligible date / required action
+
reminder
```

**Primary KPI**

```text
Failure → Successful eligibility within 30/60 days
```

The objective would be to understand whether providing users with a clear recovery path increases the probability of becoming eligible later.

---

## Experiment 2 — Personalized Onboarding

**Control**

The same questionnaire experience regardless of entry point.

**Variant**

Different onboarding and messaging depending on whether the user entered through:

```text
Apply Now
```

or:

```text
Check Eligibility
```

**Primary KPI**

```text
Questionnaire completion → Successful next step
```

Secondary metrics could include:

```text
Drop-off rate
Retry rate
Time to completion
Downstream conversion
```

---

# 11. Limitations

There are several important limitations to consider.

First, this is an **observational analysis**.

The fact that two failure reasons frequently occur together does not mean that one causes the other.

Similarly, the difference between *Apply Now* and *Check Eligibility* does not prove that the CTA itself causes a different failure profile.

The CTA may simply attract users with different characteristics.

Therefore:

> **Segmentation identifies hypotheses. Experimentation is required to establish causality.**

Additional variables such as acquisition channel, device, user history and previous product interactions could also explain part of the observed differences.

---

# 🎯 Key Takeaways

The analysis started with a relatively simple question:

> **Why are users failing the onboarding?**

But looking only at the most frequent failure reasons would have missed most of the story.

The analysis revealed that:

- **62% of failures involve multiple problems.**
- Employment and documentation constraints frequently occur together.
- Affordability behaves much more like an independent failure reason.
- Different entry points attract users with substantially different failure profiles.
- Some failures appear structural, while others may be temporary and recoverable.

The most important product opportunity is therefore not simply to **reduce the number of failures**.

It is to understand:

> **Which users can be recovered, why they failed, and what the product should do next.**

---

## 🧰 Tools & Methods

`Python` · `pandas` · `Product Analytics` · `Funnel Analysis` · `Behavioral Segmentation` · `Multi-label Analysis` · `Experimentation`

---

## 💭 Final Thought

Product Analytics is not just about measuring conversion rates.

The real value comes from moving through four stages:

> **Measure → Understand → Hypothesize → Act**

A dashboard can tell us that users are failing.

A good analysis should help us understand **why — and what we should do about it.**
