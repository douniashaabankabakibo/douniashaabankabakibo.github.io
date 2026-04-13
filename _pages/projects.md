---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: [sewing, "creative writing"]
horizontal: false
---

I see art as one of the only ways we can truly make sense of human emotion.

If my research philosophy is all about dedication and rigor, my art is about the opposite - what does it mean to be playful and wander? I've lost count of how many crafts and art forms I've tried over the years (and enjoyed). The ones that have stuck are sewing and creative writing. Music is a deep love I haven't yet tamed - I don't have the freedom in it that I crave, but I'm working on it.

A sample of work from over the years is below. And if you're ever up for a funky collaboration on a stage, reach out - that's very much my kind of thing.

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

	<!-- Generate cards for each project -->

{% if page.horizontal %}

	<div class="container">
		<div class="row row-cols-1 row-cols-md-2">
		{% for project in sorted_projects %}
			{% include projects_horizontal.liquid %}
		{% endfor %}
		</div>
	</div>
	{% else %}
	<div class="row row-cols-1 row-cols-md-3">
		{% for project in sorted_projects %}
			{% include projects.liquid %}
		{% endfor %}
	</div>
	{% endif %}
{% endif %}
</div>
