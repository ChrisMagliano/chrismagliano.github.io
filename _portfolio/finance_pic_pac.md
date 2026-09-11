---
title: "Lump Sum vs Dollar-Cost Averaging: Does Timing Really Matter?"
excerpt: "A Monte Carlo experiment comparing lump-sum investing with a gradual investment strategy."
collection: portfolio
category: "Finance"
header:
  teaser: "/images/portfolio_finance_pac_pic/finance_pac_pic1.jpg"
---

# 💰 Lump Sum vs Dollar-Cost Averaging

> **Finance & Data Science**  
> Monte Carlo Simulation · Compounding · Investment Timing · Python

## 💡 The Question

Suppose I have **€34,000** to invest over a 10-year horizon.

Is it better to invest everything immediately or gradually enter the market?

To explore this question, I compared two strategies:

- **Lump Sum (PIC):** €34,000 invested immediately.
- **Dollar-Cost Averaging (PAC):** €10,000 initially + €200/month for 10 years.

---

## 1. The Simulation

I generated **20,000 Monte Carlo scenarios** under the following assumptions:

| Parameter | Value |
|---|---:|
| Total Capital | €34,000 |
| Horizon | 10 years |
| Expected Annual Return | 7% |
| Returns | Monthly, lognormal |

Both strategies experience exactly the **same simulated market path** within each scenario.

The only difference is **when capital enters the market**.

---

## 2. The Results

| | Lump Sum | DCA |
|---|---:|---:|
| Mean Final Wealth | **€74,544** | €58,279 |
| Median Final Wealth | **€66,717** | €54,403 |
| 5th Percentile | €30,676 | **€31,464** |
| 95th Percentile | **€144,966** | €98,036 |
| Standard Deviation | €37,036 | **€21,347** |

The gradual strategy outperformed the lump-sum investment in only **2,332 out of 20,000 simulations (~12%)**.

> **Lump Sum produced higher expected wealth, but also a much wider distribution of outcomes.**

---

## 3. Why Does Lump Sum Usually Win?

The reason is relatively simple.

If the asset has a positive expected return, investing earlier gives more capital **more time to compound**.

```text
Lump Sum
€34,000 ──────────────────────────────→
          exposed for ~10 years

DCA
€10,000 ──────────────────────────────→
       + €200
          + €200
             + €200 ...
```

DCA reduces the amount exposed to the market early on.

That protects against investing everything immediately before a downturn, but also reduces participation in rising markets.

---

## 4. The Role of Return Sequence

The gradual strategy introduces another interesting effect: **the order of returns matters**.

With Lump Sum and no additional cash flows, rearranging the same set of returns does not change final wealth:

```text
(1+r₁)(1+r₂)...(1+rₙ)
```

With DCA, however, each contribution experiences a different subset of future returns.

Therefore, two market paths with similar overall performance can produce different outcomes depending on **when positive and negative returns occur relative to contributions**.

In my simulations, some of the worst DCA outcomes followed an interesting pattern:

> **Strong returns early, followed by large losses later.**

By the time the downturn arrives, much more capital has been accumulated and is exposed to the decline.

---
<div style="width: 100%; max-width: 800px; margin: 30px auto; text-align: center;">
    <img src="/images/portfolio_pic_pac/pic_pac1.jpg"
         alt="Distribution of final wealth"
         style="width: 100%;">
    <p><em></em></p>
</div>
<div style="width: 100%; max-width: 800px; margin: 30px auto; text-align: center;">
    <img src="/images/portfolio_pic_pac/pic_pac2.jpg"
         alt="Distribution of final wealth"
         style="width: 100%;">
    <p><em></em></p>
</div>

## 🎯 Key Takeaways

- Lump Sum generated higher wealth in roughly **88% of simulations**.
- DCA produced a narrower distribution of outcomes.
- Investing earlier maximizes exposure to **compound growth**.
- Gradual investing reduces **entry-timing risk**, but sacrifices part of the potential upside.
- Return sequence matters for DCA because capital enters the market at different points in time.

The trade-off is therefore not simply:

> **Safe vs Risky**

but rather:

> **Reducing timing risk vs maximizing time in the market.**

---

## 🧰 Tools & Methods

`Python` · `NumPy` · `Monte Carlo Simulation` · `Statistics` · `Compounding` · `Sequence of Returns`

---

## ⚠️ Disclaimer

This is a simplified simulation created for educational purposes while studying personal finance.

It is **not financial advice**, and real markets are considerably more complex than the assumptions used here.
