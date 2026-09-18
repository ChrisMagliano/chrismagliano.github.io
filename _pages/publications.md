---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

<section class="publications-hero">

<p class="publications-eyebrow">RESEARCH & ACADEMIC WORK</p>

<div class="publications-intro-grid">

<div>

<p class="publications-intro">
From 2022 to 2024, I pursued my <strong>PhD in Astrophysics</strong>,
focusing primarily on <strong>exoplanets</strong> and the scientific exploitation
of the PLATO space mission.
</p>

<p>
Below you can explore the research articles I have led as
<strong>first author</strong> or contributed to as a <strong>co-author</strong>.
</p>

{% if site.author.googlescholar %}
<a href="https://scholar.google.com/citations?user=kLNkJnkAAAAJ&hl=it&oi=ao"
   class="publications-scholar">
   View my Google Scholar profile →
</a>
{% endif %}

</div>

<img
  src="/images/publications_logo.jpg"
  alt="Scientific research"
  class="publications-hero-image">

</div>

</section>


<section class="publications-list">

<p class="publications-section-label">PUBLICATIONS</p>

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}

</section>
