---
layout: page
---

<ul class="posts-list">
	<li>
		<a class="post-link highlighted" href="{{ "/about" | prepend: site.baseurl }}">About</a>
	</li>
	<li>—</li>
{% for post in site.posts %}
	<li>
		<a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
	</li>
{% endfor %}
</ul>
