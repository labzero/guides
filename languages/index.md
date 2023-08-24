---
layout: default
title: Coding Style and Usage Guides
has_children: true
related_pages: none
---

## Ruby

{% assign pages = site.pages | where_exp: "item", "item.dir == '/languages/ruby/'" %}
{% for page in pages %}
- [{{ page.title or page.name or page.url or 'asdf' }}]({{page.url | relative_url }})
{% endfor %}

## JavaScript / TypeScript / ECMAScript
{% assign pages = site.pages | where_exp: "item", "item.dir == '/languages/javascript/'" %}
{% for page in pages %}
- [{{ page.title or page.name or page.url or 'asdf' }}]({{page.url | relative_url }})
{% endfor %}

## CSS

[CSS](css)

## iOS

[iOS](ios)
