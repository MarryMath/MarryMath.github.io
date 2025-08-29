---
layout: page
title: courses
permalink: /courses/
description: A growing collection of your  course.
nav: true
nav_order: 7
display_categories: [work, fun]
horizontal: false
---

<!-- pages/courses.md -->
<div class="projects">
{% if site.enable_project_categories and site.display_categories %}
  <!-- Display categorized projects -->
  <div class="categories">
  {% for category in site.display_categories %}
    <h2 class="category">{{ category }}</h2>
    {% assign categorized_projects = site.courses | where: "category", category %}
    {% assign sorted_projects = categorized_projects | sort: "importance" %}
    <!-- Generate cards for each project -->
    <div class="grid">
      {% for project in sorted_projects %}
        {% include courses.html %}
      {% endfor %}
    </div>
  {% endfor %}
  </div>
{% else %}
  <!-- Display projects without categories -->
  {% assign sorted_projects = site.courses | sort: "importance" | reverse %}
  <div class="grid">
    {% for project in sorted_projects %}
      {% include courses.html %}
    {% endfor %}
  </div>
{% endif %}
</div>

