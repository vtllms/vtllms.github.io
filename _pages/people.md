---
layout: page
title: people
permalink: /people/
description: Members of the lab
nav: true
nav_order: 1
display_categories: [Faculty, fun]
horizontal: false
---

<!-- pages/people.md -->
<div class="people">
{% if site.enable_person_categories and page.display_categories %}
  <!-- Display categorized people -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_people = site.people | where: "category", category %}
  {% assign sorted_people = categorized_people | sort: "importance" %}
  <!-- Generate cards for each person -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for person in sorted_people %}
      {% include people_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-4">
    {% for person in sorted_people %}
      {% include people.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display people without categories -->

{% assign sorted_people = site.people | sort: "importance" %}

  <!-- Generate cards for each person -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for person in sorted_people %}
      {% include people_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-4">
    {% for person in sorted_people %}
      {% include people.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
