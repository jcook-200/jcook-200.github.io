---
layout: single
author_profile: true
title: "Engineering Portfolio"
classes: wide

header:
  teaser: /assets/images/bio-photo.JPG
---

Welcome to my portfolio! My name is Josh and I am a second year engineering physics student at UBC. 

## Projects

<div class="entries-grid">
  {% for post in site.projects %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
