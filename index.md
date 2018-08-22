<h1>{{ site.name }}</h1>

<ul>
{% for file in site.static_files | where_exp: "file", "file.path contains 'tracks'" %}
  <li><a href="{{ site.basepath }}{{ file.path }}">{{ file.basename }}</a></li>
{% endfor %}
</ul>
