---
layout: archive
title: "Portfolio"
permalink: /portfolio/
author_profile: false
---

{% include base_path %}

{% assign sorted_portfolio = site.portfolio | sort: "order" %}

<div class="portfolio-grid">
  {% for post in sorted_portfolio %}
    <div class="portfolio-card">
      {% if post.image %}
        <img src="{{ post.image | relative_url }}" alt="{{ post.title }} thumbnail">
      {% endif %}

      {% if post.caption %}
        <figcaption>{{ post.caption }}</figcaption>
      {% endif %}
      
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      {% if post.excerpt %}
        <p>{{ post.excerpt }}</p>
      {% endif %}
    </div>
  {% endfor %}
</div>

