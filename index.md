---
layout: page
subtitle: Info, projects, essays
---

<h1>Strict Machine</h1>

<ul class="posts-list">
	<li>
		<a class="contact-button" href="/contact">Contact Me</a>
	</li>
</ul>

<ul class="posts-list">
{% for post in site.posts %}
	<li>
		<p class="post-date">{{ post.date | date: "%A, %B %e, %Y" }}</p>
		<a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
		<p class="post-link-subtitle">{{ post.subtitle}}</p>
	</li>
{% endfor %}
</ul>
