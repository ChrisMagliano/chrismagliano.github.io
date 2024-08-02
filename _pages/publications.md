---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
<div class="wordwrap">Below you can access to the articles I have led as first author.</div>
  <div class="wordwrap">You can also find all my articles on <a href="{{https://scholar.google.com/citations?user=kLNkJnkAAAAJ&hl=it&oi=ao}}">my Google Scholar profile</a>.</div>
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
