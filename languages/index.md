---
layout: default
title: Programming Language Guides
# nav_order: 15
has_children: true
related_pages: none
---

# coding style and usage guides


{% for kern in site.collections %}
  <pre>{{ kern | jsonify | escape }}</pre>
{% endfor %}

## all

<pre>
    pages: {{ site.pages | jsonify | escape }}
</pre>


{% for page in site.pages %}
```json
  {{ page | jsonify |escape }}
```
{% endfor %}


## auto nav

### Ruby

{% assign pages = site.pages | where_exp: "item", "item.dir == '/languages/ruby/'" %}
{% for page in pages %}
- [{{ page.title or page.name or page.url or 'asdf' }}]({{page.url}})
{% endfor %}
