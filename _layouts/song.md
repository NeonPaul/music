---
layout: default
---

<h1>{{ page.title }}</h1>

{% if page.track %}
<audio id="audio" preload="auto" tabindex="0" controls="" style="width:100%">
  <source src="{{ site.baseurl }}/{{ page.track }}">
</audio>
<p><a href="{{ site.baseurl }}/{{ page.track }}" download>Download</a></p>
{% endif %}

{% assign splitContent = content | split: '<hr />' %}
{% assign lyrics = splitContent | last %}
{% if splitContent.size > 1 %}
{{ splitContent | first }}
{% endif %}

<pre>{{ lyrics }}</pre>
