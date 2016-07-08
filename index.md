---
layout: page
---

<ul class="posts-list">
	<li>
		<a class="post-link highlighted" href="{{ "/about" | prepend: site.baseurl }}">About</a>
	</li>
</ul>

<h2>Projects</h2>
<ul class="posts-list">
	<li>
		<a class="post-link" href="{{ "/Vimmy.safariextension" | prepend: site.baseurl }}">Vimmy.safariextension</a>
	</li>
	<li>
		<a class="post-link" href="{{ "/Scattegories" | prepend: site.baseurl }}">Scattegories</a>
	</li>
</ul>

<h2>Essays</h2>

<ul class="posts-list">
{% for post in site.posts %}
	<li>
		<a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
	</li>
{% endfor %}
</ul>
