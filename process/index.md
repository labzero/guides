## Process and playbook guides

{% assign pages = site.pages | where_exp: "item", "item.dir == '/process/'" %}
{% for page in pages %}
- title {{page.title}}
- name {{ page.name }}
- whole {{ page | jsonify | escape }}
- [{{ page.title or page.name or page.url or 'asdf' }}]({{page.url | relative_url }})
{% endfor %}
