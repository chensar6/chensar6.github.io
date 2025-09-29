---
layout: page
title: d&d posts
permalink: /dndposts/
description: D&D materials. Currently under construction.
nav: true
nav_order: 2
display_categories: [resources, lore]
horizontal: false
---

This page is under construction but will soon be populated with D&D resources for those playing in the group I am DMing.

<!-- pages/dndposts.md -->
<div class="projects">
{% if site.enable_dndpost_categories and page.display_categories %}
  <!-- Display categorized dndposts -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_dndposts = site.dndposts | where: "category", category %}
  {% assign sorted_dndposts = categorized_dndposts | sort: "importance" %}
  <!-- Generate cards for each dndpost -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for dndpost in sorted_dndposts %}
      {% include dndposts_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for dndpost in sorted_dndposts %}
      {% include dndposts.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display dndposts without categories -->

{% assign sorted_dndposts = site.dndposts | sort: "importance" %}

  <!-- Generate cards for each dndpost -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for dndpost in sorted_dndposts %}
      {% include dndposts_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for dndpost in sorted_dndposts %}
      {% include dndposts.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
