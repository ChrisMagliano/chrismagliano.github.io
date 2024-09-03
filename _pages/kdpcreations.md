---
layout: archive
title: "KDP Creations"
permalink: /kdpcreations/
author_profile: true
---

{% if site.author.googlescholar %}
Welcome to my KDP Creations page! In my free time I love self-publishing my own books by means of <a href="https://kdp.amazon.com/">Amazon Kindle Direct Publishing</a> service. Here you will find a collection of my self-published books. 
![Illustration of combining vision and language modalities](/images/kdp_creations_logo.jfif){:.align-right width="300px"}

Stay tuned for updates and new projects! 🌌✨
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
