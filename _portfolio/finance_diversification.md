---
title: "How Diversification Can Increase Compound Growth"
excerpt: "How correlation between assets can reduce volatility drag and increase long-term compound returns."
collection: portfolio
category: "Finance"
header:
teaser:
---

# 📊 How Diversification Can Increase Compound Growth

> **Finance & Statistics**  
> Portfolio Theory · Correlation · Volatility · Compounding

## 💡 The Question

We have already seen that volatility can reduce compound growth through the **volatility drag**.

But what happens when we combine multiple assets?

Consider two assets with identical characteristics:

| | Asset A | Asset B |
|---|---:|---:|
| Expected Return | 7% | 7% |
| Volatility | 15% | 15% |

We build a portfolio:

> **50% Asset A + 50% Asset B**

The expected return remains **7%**.

What changes is their **correlation**.

---

## 1. No Real Diversification

Suppose the two assets are perfectly correlated:

> **ρ = 1**

They always move together.

The portfolio therefore has:

```text
Expected Return ≈ 7%
Volatility      ≈ 15%
CAGR            ≈ 5.9%
```

Combining the assets provides essentially **no diversification benefit**.

---

## 2. Real Diversification

Now assume:

> **ρ = 0.2**

The assets no longer move perfectly together.

The expected return remains unchanged, but portfolio volatility falls:

```text
Expected Return ≈ 7%
Volatility      ≈ 11%
CAGR            ≈ 6.4%
```

That's approximately **+0.5 percentage points of annual compound growth** without increasing expected return.

---

## 3. Why?

For a two-asset portfolio:

```text
σp² = wA²σA² + wB²σB² + 2wAwBσAσBρ
```

Correlation enters directly into portfolio variance.

Lower correlation → lower covariance → lower portfolio volatility.

And since compound growth can be approximated as:

```text
CAGR ≈ μ - σ²/2
```

reducing volatility also reduces the **volatility drag**.

```text
Lower correlation
       ↓
Lower portfolio volatility
       ↓
Lower volatility drag
       ↓
Higher compound growth
```

---

## 🎯 Key Takeaway

Diversification is not simply about owning more assets.

> **The important question is how those assets move relative to each other.**

Two perfectly correlated investments provide little diversification benefit.

Combining assets with lower correlation can instead reduce portfolio volatility **without necessarily reducing expected return**.

And lower volatility means less volatility drag and potentially higher long-term compound growth.

> **Diversification doesn't only make the journey smoother. It can make compounding more efficient.**

---

## 🧰 Tools & Methods

`Portfolio Theory` · `Statistics` · `Correlation` · `Covariance` · `Volatility` · `Compounding`
