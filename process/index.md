## Process and playbook guides

{% assign pages = site.pages | where_exp: "item", "item.dir == '/process/'" %}
{% for page in pages %}
  {% if page.name != 'index.md' %}
    - [{{ page.title or page.name or page.url }}]({{ page.url | relative_url }})
  {% endif %}
{% endfor %}
