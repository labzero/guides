---
layout: default
title: Programming Language Guides
# nav_order: 15
has_children: true
---

# coding style and usage guides

{% for page in site.pages.languages %}
  <p>{{ page.title }}</p>
{% endfor %}

{% for kern in site.collections %}
  <p>{{ kern | markdownify }}</p>
{% endfor %}
