---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if site.author.googlescholar %}
Welcome to my publications page 📰! Below you can access to the articles I have led as first author 👨‍🔬.
![Illustration of combining vision and language modalities](/images/publications_logo.jpg){:.align-right width="300px"}
You can also find all the works I have contributed to on my [Google Scholar](https://scholar.google.com/citations?user=kLNkJnkAAAAJ&hl=it&oi=ao) profile.
{% endif %}

{% include base_path %}

{% for post in site.publications reversed %}
  {% include archive-single.html %}
{% endfor %}
