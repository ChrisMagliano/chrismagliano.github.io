---
title: "Your Conversion Rate Can Drop Even When Everything Is Improving"
excerpt: "How changes in traffic mix can make overall conversion decline while every segment improves."
collection: portfolio
category: "Product Analytics"
---

# 📉 Your Conversion Rate Can Drop Even When Everything Is Improving

> **Product Analytics & Statistics**  
> Conversion Rate · Segmentation · Mix Effect · Simpson's Paradox

## 💡 The Problem

Imagine this scenario:

- 📱 Mobile conversion improves
- 💻 Desktop conversion improves
- 📉 Overall conversion declines

Bug?

No. **Statistics.**

Overall Conversion Rate depends not only on how each segment performs, but also on **how much each segment weighs in the total traffic**.

---

## 1. Conversion Rate Is a Weighted Average

Suppose traffic comes from Mobile and Desktop:

```text
Total CVR =
Mobile CVR × Mobile Traffic Share
+
Desktop CVR × Desktop Traffic Share
```

Therefore, total CVR can change because of two different mechanisms.

### Performance Effect

Conversion changes **within each segment**.

```text
Mobile:  4% → 5%
Desktop: 8% → 9%
```

Both improvements push overall CVR upward.

### Mix Effect

The **composition of traffic** changes.

If Mobile structurally converts less than Desktop and its traffic share increases substantially, more weight is assigned to the lower-converting segment.

That can push overall CVR downward.

---

## 2. A Numerical Example

Consider:

| | Previous Year | Current Year |
|---|---:|---:|
| Mobile CVR | 4.0% | **5.0%** |
| Desktop CVR | 8.0% | **9.0%** |
| Mobile Traffic Share | 40% | **80%** |
| Desktop Traffic Share | 60% | **20%** |

Both segments improve:

```text
Mobile  → +25%
Desktop → +12.5%
```

But overall CVR changes from:

```text
Previous Year
4% × 40% + 8% × 60%
= 6.4%
```

to:

```text
Current Year
5% × 80% + 9% × 20%
= 5.8%
```

So:

> **Every segment improved, but total CVR dropped from 6.4% to 5.8%.**

---

## 3. What Happened?

Performance improved.

But at the same time, traffic shifted heavily toward **Mobile**, the segment with the structurally lower conversion rate.

```text
Better segment performance
        ↑

More traffic on lower-CVR segment
        ↓

Overall CVR
        ↓
```

The negative **mix effect** was stronger than the positive **performance effect**.

This is closely related to **Simpson's Paradox**: an aggregate trend can move in the opposite direction from the trends observed within individual groups.

---

## 🎯 Product Analytics Takeaway

When an aggregate KPI changes, segmentation should be one of the first checks.

Instead of simply asking:

> **"Why is conversion down?"**

I would separate two questions:

> **Did users become less likely to convert within each segment?**

and:

> **Or did the composition of users change?**

These represent two completely different problems — and require different product decisions.

---

## 🧰 Tools & Methods

`Product Analytics` · `Statistics` · `Segmentation` · `Weighted Averages` · `Simpson's Paradox` · `Conversion Analysis`
