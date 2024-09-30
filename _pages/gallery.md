---
layout: page
permalink: /Gallery/
title: Gallery
description: Welcome to my Gallery, a curated space where I share my poetry, photography, and other intriguing creations. 
nav: true
nav_order: 3
display_categories: [Poetry, Art]
horizontal: false
---

<!-- pages/gallery.md -->
<div class="galleries">
{% if site.enable_gallery_categories and page.display_categories %}
  <!-- Display categorized galleries -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_galleries = site.galleries | where: "category", category %}
  {% assign sorted_galleries = categorized_galleries | sort: "importance" %}
  <!-- Generate cards for each gallery -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for gallery in sorted_galleries %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for gallery in sorted_galleries %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display galleries without categories -->

{% assign sorted_galleries = site.galleries | sort: "importance" %}

  <!-- Generate cards for each gallery -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for gallery in sorted_galleries %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for gallery in sorted_galleries %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>


