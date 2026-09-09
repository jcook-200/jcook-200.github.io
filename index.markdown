---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
author_profile: true
title: "Engineering Portfolio"
classes: wide

header:
  tease: /assests/images/bio-photo.JPG

  entries_layout: grid
---

{% assign projects = site.projects | sort: 'date' | reverse %}
<div class="entries-grid">
  {% for project in projects %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>
