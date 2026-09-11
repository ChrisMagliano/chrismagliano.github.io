---
title: "Compound Interest and Its Evil Twin: Inflation"
excerpt: "How inflation compounds over time and silently erodes the real value of long-term investments."
collection: portfolio
category: "Finance"
header:
teaser:"/images/portfolio_compound_interest/compound_interest.jpg"
---

# 🎭 Compound Interest and Its Evil Twin

> **Finance & Data Science**  
> Inflation · Compounding · Monte Carlo · AR(1) Process

## 💡 The Problem

Compound interest is one of the most powerful forces in long-term investing.

But it has an evil twin:

> **Compound inflation.**

Imagine investing **€30,000** today at 7% per year.

After 30 years:

```text
Nominal Wealth ≈ €228,000
```

Impressive.

But with average inflation of 3%, those €228,000 would have the purchasing power of roughly:

```text
Real Wealth ≈ €94,000
```

The portfolio grew enormously in nominal terms, but inflation absorbed a large part of that growth.

---

## 1. Adding Uncertainty

Inflation is not constant.

To explore its long-term impact, I generated **5,000 Monte Carlo simulations** over 30 years.

### Market

```text
Expected Return: 7%
Volatility:      15%
```

### Inflation

Instead of assuming constant inflation, I modeled it as an **AR(1) process** with persistence:

```text
ρ = 0.5
```

This gives inflation "memory": after a shock, inflation tends to remain elevated before gradually returning toward its long-term level.

I also introduced:

```text
Inflation target: 2%
Annual shock probability: 5%
Shock magnitude: +4%
```

---

## 2. Nominal Wealth vs Real Wealth

The simulation produces two very different pictures.

### Nominal Wealth

This is what the portfolio statement shows:

```text
Initial Capital
      ↓
Market Returns
      ↓
Nominal Final Wealth
```

### Real Wealth

This measures what that money can actually buy:

```text
Nominal Final Wealth
        ↓
Accumulated Inflation
        ↓
Real Purchasing Power
```

After 30 years, the median real wealth is approximately **half the nominal value**.

> Inflation silently absorbs a significant part of long-term compound growth.

In some particularly unfavorable simulations, real final wealth can even fall below the initial purchasing power.

---

## 3. Why Does Inflation Hurt So Much?

Because inflation compounds too.

Real wealth is approximately:

```text
Real Wealth =
Nominal Wealth / (1 + inflation)^t
```

A seemingly small annual inflation rate becomes substantial over long horizons.

At 3% inflation:

```text
€1 today
≈
€2.43 in 30 years
```

just to maintain the same purchasing power.

---
<div style="width: 100%; max-width: 800px; margin: 30px auto; text-align: center;">
    <img src="/images/portfolio_compound_interest/compound_interest.jpg"
         alt="Distribution of final wealth"
         style="width: 100%;">
    <p><em></em></p>
</div>

## 🎯 Key Takeaway

Long-term investing is not only about maximizing nominal returns.

The real objective is:

> **Preserving and increasing purchasing power.**

Compound returns work in your favor.

Compound inflation works against you.

This is why nominal wealth alone can provide a misleading picture of long-term financial outcomes.

> **What matters is not how many euros you will have, but what those euros will be able to buy.**

---

## 🧰 Tools & Methods

`Python` · `Monte Carlo Simulation` · `Time Series` · `AR(1)` · `Inflation` · `Compounding`
