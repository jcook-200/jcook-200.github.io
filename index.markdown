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

{% assign projects = site.projects | sort: 'date' | reverse %}
<div class="entries-grid">
  {% for project in projects %}
    {% include archive-single.html type="grid" post=projects%}
  {% endfor %}
</div>
