---
layout: page
title: Blog
---

<section>
	<div style="text-align: center;">
		<span class="hlink " onclick="window.location='/whoami/'">About</span> • 
		<span class="hlink " onclick="window.location='/whoami/blog'">Blog</span> • 
		<span class="hlink " onclick="window.location='/whoami/projects'">Projects</span>
	</div>
	<div></div>
</section>

<section>

	<h3 class="code">Category m</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'm' %}

			<ul>
				<li>
					<div class="post-date code">
						<span>{{ post.date | date: "%b %d" }}</span>
					</div>
					<div class="title">
						<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
					</div>
				</li>
			</ul>
			
			{% endif %}
		{% endfor %}
	{% endfor %}


	<h3 class="code">Category n</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'n' %}

			<ul>
				<li>
					<div class="post-date code">
						<span>{{ post.date | date: "%b %d" }}</span>
					</div>
					<div class="title">
						<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
					</div>
				</li>
			</ul>
			
			{% endif %}
		{% endfor %}
	{% endfor %}


	<h3 class="code">Category p</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'p' %}

			<ul>
				<li>
					<div class="post-date code">
						<span>{{ post.date | date: "%b %d" }}</span>
					</div>
					<div class="title">
						<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
					</div>
				</li>
			</ul>
			
			{% endif %}
		{% endfor %}
	{% endfor %}

</section>

<!-- section>
	{% for post in site.posts %}
		{% unless post.next %}
			<h3 class="code">{{ post.date | date: '%Y' }}</h3>
		{% else %}
			{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
			{% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
			{% if year != nyear %}
				<h3 class="code">{{ post.date | date: '%Y' }}</h3>
			{% endif %}
		{% endunless %}

		<ul>
			<li>
				<div class="post-date code">
					<span>{{ post.date | date: "%b %d" }}</span>
				</div>
				<div class="title">
					<a href="{{ post.url | prepend: site.baseurl | prepend: site.url }}">{{ post.title }}</a>
				</div>
			</li>
		</ul>
	{% endfor %}
</section -->


