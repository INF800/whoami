---
layout: page
title: Blog
---

<section>
	<div style="text-align: center;">
		<span class="hlink " onclick="window.location='/whoami/'">About</span> • 
		<span class="hlink " onclick="window.location='/whoami/blog'" style="color: rgba(0, 0, 0, 0.7)">Blog</span> • 
		<span class="hlink " onclick="window.location='/whoami/projects'">Projects</span>
	</div>
	<div></div>
</section>

<!--section>
	<div class="title">
		Sorry for inconvinienece. Site is under reconstruction. To see some of old blogs <a href="https://www.kaggle.com/l0new0lf/machine-learning-data-science-bookmarks">check this link</a>
	</div>
</section -->

<section>
	<!-- 
	<h3 class="code">Deep Learning with Flax</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'Flax' %}

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
	--> 
	

	<h3 class="code">Statistics</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'Statistics' %}

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

	<h3 class="code">WebGL</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'WebGL' %}

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

	<h3 class="code">Reinforcement Learning</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'Reinforcement Learning' %}

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

	
	<h3 class="code">Personal</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'Personal' %}

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
	
	
	<!-- 
	<h3 class="code">DSA (Leetcode)</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'dsa' %}

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
	-->
	
	<!--
	<h3 class="code">Flutter</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'flutter' %}

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
	-->

	<!--
	<h3 class="code">Miscellaneous</h3>
	{% for post in site.posts %}
		{% for c in post.categories %}
			{% if c == 'Misc' %}

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
	-->

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


