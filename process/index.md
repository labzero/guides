> See the [main site page](../) for a better listing of these guides.

## Process and playbook guides
<!---
The below Jekyll liquid code will auto generate the contents of this index page.
It simply lists out links to the files in this directory.
If you add a new file in this directory it will be automatically added.
--!>

{% assign pages = site.pages | where_exp: "item", "item.dir == '/process/'" %}
{% for page in pages %}
{% if page.name != 'index.md' %}
<!-- do not correct this whitespace -->
- [{{ page.title or page.name or page.url }}]({{ page.url | relative_url }})
{% endif %}
{% endfor %}
