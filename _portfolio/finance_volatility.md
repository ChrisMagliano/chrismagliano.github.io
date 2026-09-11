---
title: "Same Return, Different Wealth: The Hidden Cost of Volatility"
excerpt: "How two investors can achieve the same 7% average return and end up with very different wealth."
collection: portfolio
---

# 📉 Same Return, Different Wealth

> **Finance & Data Science**  
> Monte Carlo Simulation · Compounding · Volatility · Python

## 💡 The Question

Two people invest for **10 years**.

Both start with **€10,000** and achieve an average annual return of **7%**.

Yet one almost doubles the initial capital, while the other doesn't.

> **How is that possible?**

The answer is **volatility**.

---

## 1. The Experiment

I simulated two investment scenarios:

| | Scenario A | Scenario B |
|---|---:|---:|
| Expected annual return | 7% | 7% |
| Annual volatility | 0% | 20% |
| Initial capital | €10,000 | €10,000 |
| Horizon | 10 years | 10 years |

For Scenario B, I generated **100,000 Monte Carlo simulations** using lognormal returns to reproduce the multiplicative nature of compound growth.

---

## 2. The Results

| | Scenario A | Scenario B |
|---|---:|---:|
| Average Final Wealth | €19,671 | €19,658 |
| Median Final Wealth | €19,671 | €16,072 |
| Average CAGR | 7% | ~7% |
| Median CAGR | 7% | ~5% |

At first sight, volatility seems irrelevant: **average wealth is almost identical**.

But the median tells a different story.

> The typical investor in the volatile scenario grows at approximately **5% instead of 7%**.

---

## 3. Why?

Investment returns compound **multiplicatively**.

Consider two years:

```text
Year 1: -50%
Year 2: +100%
```

The arithmetic average return is:

```text
(-50% + 100%) / 2 = +25%
```

But actual wealth behaves differently:

```text
€100 × 0.50 × 2.00 = €100
```

The investor made **0%**.

The geometric return correctly captures this:

```text
(0.50 × 2.00)^(1/2) - 1 = 0%
```

> **The arithmetic mean describes average returns.  
> The geometric mean describes the growth of wealth.**

---

## 4. The Volatility Drag

Under standard assumptions, the geometric growth rate can be approximated by:

```text
Geometric Return ≈ Arithmetic Return - σ²/2
```

With 20% volatility:

```text
σ²/2 = 0.20² / 2 = 2%
```

Therefore:

```text
7% - 2% ≈ 5%
```

This difference is known as **volatility drag**.

The higher the volatility, the larger its impact on compound growth.

---

## 5. Mean vs Median

Why does average final wealth remain close to €19,700?

Because volatile returns generate an **asymmetric distribution**.

A small number of extremely successful paths pull the average upward, while the median represents the outcome of the typical simulated investor.

That's why:

```text
Mean   ≈ €19,658
Median ≈ €16,072
```

Looking only at the average can therefore hide a large difference in typical outcomes.

---

## 🎯 Key Takeaways

- The same average return does **not** imply the same compound growth.
- Volatility reduces the typical geometric growth rate.
- The effect is known as **volatility drag**.
- Mean and median wealth can diverge significantly in volatile markets.
- In long-term investing, the **distribution of outcomes** matters as much as the average return.

> **It is not only how much an investment returns that matters, but also how that return is generated.**

---

## 🧰 Tools & Methods

`Python` · `NumPy` · `Monte Carlo Simulation` · `Statistics` · `Compounding` · `Geometric Brownian Motion`
