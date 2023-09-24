---
layout: page
title: Coding Style and Usage Guides
has_children: true
related_pages: none
redirect_from:
  - /languages/ruby
  - /languages/javascript
  - /languages/ruby/
  - /languages/javascript/
---

{% comment %}
This page generates a listing of pages in its sub-directories under each heading.
{% endcomment %}

## Ruby

{% assign pages = site.pages | where_exp: "item", "item.dir == '/languages/ruby/'" %}
{% for page in pages %}
  {% unless page.name == "redirect.html" %}
- [{{ page.title or page.name or page.url }}]({{page.url | relative_url }})
  {% endunless %}
{% endfor %}

## JavaScript / TypeScript / ECMAScript
{% assign pages = site.pages | where_exp: "item", "item.dir == '/languages/javascript/'" %}
{% for page in pages %}
  {% unless page.name == "redirect.html" %}
- [{{ page.title or page.name or page.url }}]({{page.url | relative_url }})
  {% endunless %}
{% endfor %}

## Others

- [CSS](css)
