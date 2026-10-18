---
layout: archive
title: "Tools"
permalink: /tools/
author_profile: true
---

{% include base_path %}

<style>
  .tools-page {
    font-family: inherit;
  }

  /* HERO SECTION */

  .tools-hero {
    margin: 10px 0 38px;
  }

  .tools-eyebrow {
    color: #2563eb;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  .tools-hero h2 {
    font-size: 2rem;
    margin: 0 0 14px;
    border: none;
  }

  .tools-hero p {
    color: #64748b;
    font-size: 15px;
    line-height: 1.8;
    max-width: 680px;
  }

  /* TOOLS GRID */

  .tools-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 22px;
    margin: 30px 0;
    align-items: stretch;
  }

  /* TOOL CARDS */

  .tool-card {
    display: flex;
    flex-direction: column;
    min-width: 0;
    height: 100%;
    padding: 26px;
    border: 1px solid #e2e8f0;
    border-radius: 16px;
    background: #ffffff;
    transition: transform .2s ease, box-shadow .2s ease;
  }

  .tool-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 30px rgba(15,23,42,.08);
  }

  .tool-card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 24px;
  }

  .tool-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 52px;
    height: 52px;
    background: #eff6ff;
    border-radius: 12px;
    font-size: 25px;
  }

  /* STATUS BADGES */

  .tool-status {
    font-size: 11px;
    font-weight: 700;
    padding: 6px 10px;
    border-radius: 20px;
    background: #dcfce7;
    color: #166534;
    white-space: nowrap;
  }

  .tool-status.soon {
    background: #f1f5f9;
    color: #64748b;
  }

  /* CARD CONTENT */

  .tool-card h3 {
    font-size: 21px;
    margin: 0 0 12px;
    border: none;
    line-height: 1.35;
  }

  .tool-description {
    color: #64748b;
    font-size: 14px;
    line-height: 1.7;
    margin-bottom: 22px;
    flex-grow: 1;
  }

  /* TAGS */

  .tool-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
    margin-bottom: 24px;
  }

  .tool-tag {
    background: #f1f5f9;
    color: #475569;
    border-radius: 6px;
    padding: 5px 9px;
    font-size: 11px;
    font-weight: 600;
  }

  /* BUTTONS */

  .tool-button {
    display: block;
    text-align: center;
    padding: 13px 16px;
    background: #2563eb;
    color: #ffffff !important;
    border-radius: 9px;
    font-size: 14px;
    font-weight: 700;
    text-decoration: none !important;
    transition: background .2s ease;
    margin-top: auto;
  }

  .tool-button:hover {
    background: #1d4ed8;
    color: #ffffff !important;
  }

  .tool-button.disabled {
    background: #f1f5f9;
    color: #94a3b8 !important;
    cursor: default;
  }

  /* RESPONSIVE */

  @media (max-width: 700px) {
    .tools-grid {
      grid-template-columns: 1fr;
      gap: 18px;
    }

    .tool-card {
      padding: 20px;
    }

    .tools-hero h2 {
      font-size: 1.6rem;
    }
  }
</style>

<div class="tools-page">

  <!-- HERO -->

  <section class="tools-hero">

    <div class="tools-eyebrow">
      Interactive Analytics Tools
    </div>

    <h2>Analytics Playground</h2>

    <p>
      A collection of interactive tools designed to make
      experimentation, statistics, and data-driven
      decision-making more accessible.
      Explore, experiment, and turn data into insights.
    </p>

  </section>

  <!-- TOOLS GRID: ALL FOUR CARDS -->

  <div class="tools-grid">

    <!-- 1. IMPACT ANALYZER -->

    <article class="tool-card">

      <div class="tool-card-header">
        <div class="tool-icon">🧪</div>
        <span class="tool-status">AVAILABLE</span>
      </div>

      <h3>Impact Analyzer</h3>

      <p class="tool-description">
        Compare Control and Treatment groups, measure
        conversion uplift, and evaluate statistical
        significance with clear, educational explanations.
      </p>

      <div class="tool-tags">
        <span class="tool-tag">A/B Testing</span>
        <span class="tool-tag">Statistics</span>
        <span class="tool-tag">Product Analytics</span>
      </div>

      <a class="tool-button"
         href="{{ '/tools/impact-analyzer/' | relative_url }}">
        Launch Tool ↗
      </a>

    </article>

    <!-- 2. SAMPLE SIZE CALCULATOR -->

    <article class="tool-card">

      <div class="tool-card-header">
        <div class="tool-icon">📊</div>
        <span class="tool-status">AVAILABLE</span>
      </div>

      <h3>Sample Size Calculator</h3>

      <p class="tool-description">
        Estimate the sample size required to detect
        meaningful changes in conversion rates, based
        on statistical power and minimum detectable effect.
      </p>

      <div class="tool-tags">
        <span class="tool-tag">Experiment Design</span>
        <span class="tool-tag">Statistical Power</span>
      </div>

      <a class="tool-button"
         href="{{ '/tools/sample-size-calculator/' | relative_url }}">
        Launch Tool ↗
      </a>

    </article>

    <!-- 3. COMPOUND INTEREST SIMULATOR -->

    <article class="tool-card">

      <div class="tool-card-header">
        <div class="tool-icon">📈</div>
        <span class="tool-status">AVAILABLE</span>
      </div>

      <h3>Compound Interest Simulator</h3>

      <p class="tool-description">
        Explore how investments grow over time through
        compound interest, recurring contributions, and
        different compounding frequencies. Visualize
        investment growth and the impact of inflation
        with interactive charts and educational insights.
      </p>

      <div class="tool-tags">
        <span class="tool-tag">Finance</span>
        <span class="tool-tag">Compound Interest</span>
        <span class="tool-tag">Financial Modeling</span>
      </div>

      <a class="tool-button"
         href="{{ '/tools/compound-interest-simulator/' | relative_url }}">
        Launch Tool ↗
      </a>

    </article>

    <!-- 4. REGRESSION LAB -->

    <article class="tool-card">

      <div class="tool-card-header">
        <div class="tool-icon">📉</div>
        <span class="tool-status">AVAILABLE</span>
      </div>

      <h3>Regression Lab</h3>

      <p class="tool-description">
        Explore regression modeling through interactive
        data visualization. Generate synthetic datasets
        or upload your own CSV, compare linear and
        polynomial models, and evaluate predictive
        performance using R², MAE, RMSE, and residual analysis.
      </p>

      <div class="tool-tags">
        <span class="tool-tag">Machine Learning</span>
        <span class="tool-tag">Regression</span>
        <span class="tool-tag">Predictive Modeling</span>
      </div>

      <a class="tool-button"
         href="{{ '/tools/regression-lab/' | relative_url }}">
        Launch Tool ↗
      </a>

    </article>

  </div>
  <!-- END TOOLS GRID -->

</div>
<!-- END TOOLS PAGE -->
