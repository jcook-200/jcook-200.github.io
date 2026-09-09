---
layout: single
author_profile: true
title: "Engineering Portfolio"
classes: wide

header:
  teaser: /assets/images/bio-photo.JPG
---

Welcome to my portfolio.

## Projects

<div class="entries-grid">
  {% for post in site.projects %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
