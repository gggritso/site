---
layout: page
subtitle: Info, projects, essays
---

<h1>George Gritsouk</h1>

<ul class="posts-list">
	<li>
		<a class="post-link" href="/contact">Contact</a>
	</li>
</ul>

<hr />

<ul class="posts-list">
{% for post in site.posts %}
	<li>
		<a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
	</li>
{% endfor %}
</ul>
