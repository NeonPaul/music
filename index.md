<h1>{{ site.name }}</h1>

{% assign tracks = site.static_files | where_exp: "file", "file.path contains 'tracks'" %}

<audio id="audio" preload="auto" tabindex="0" controls="" >
  <source src="{{ site.baseurl }}{{ tracks[0].path }}">
</audio>

<h2>Tracks</h2>
<ul>
{% for file in tracks %}
  <li><a href="{{ site.baseurl }}{{ file.path }}">{{ file.basename }}</a></li>
{% endfor %}
</ul>

<h2>Pages</h2>
<ul>
{% for page in site.songs %}
  <li><a href="{{ site.baseurl }}{{ page.url }}">{{ page.title }}</a></li>
{% endfor %}
</ul>

<script>
document.body.addEventListener('click', e => {
  if(e.target.pathname && e.target.pathname.match(/(wav|mp3)$/)){
    const audio = document.querySelector('#audio');

    audio.src = e.target.pathname;
    audio.load();
    audio.play();
    e.preventDefault();
  }
});
</script>
