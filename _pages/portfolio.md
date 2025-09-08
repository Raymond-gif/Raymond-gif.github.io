---
layout: splash
title: "Portfolio"
permalink: /portfolio/
header:
---

<style>
  .under-construction {
    text-align: center;
    background-color: #fff3cd;
    color: #856404;
    border: 1px solid #ffeeba;
    padding: 2rem;
    border-radius: 12px;
    font-size: 1.5rem;
    margin-bottom: 3rem;
  }

  .portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 2rem;
  }

  .portfolio-card {
    background-color: #f8f9fa;
    border-radius: 12px;
    padding: 1rem;
    box-shadow: 0 6px 20px rgba(0,0,0,0.1);
    transition: transform 0.2s;
  }

  .portfolio-card:hover {
    transform: translateY(-5px);
  }

  .portfolio-card img {
    width: 100%;
    height: 180px;
    object-fit: cover;
    border-radius: 8px;
    margin-bottom: 1rem;
  }

  .portfolio-card h3 {
    font-size: 1.2rem;
    margin: 0.5rem 0;
  }

  .portfolio-card p {
    font-size: 0.95rem;
    color: #555;
  }

  .placeholder-img {
    background-color: #ddd;
    width: 100%;
    height: 180px;
    border-radius: 8px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #666;
    font-size: 1rem;
    margin-bottom: 1rem;
  }
</style>

<div class="under-construction">
  ⚠️ This portfolio is under construction. Content coming soon! ⚠️
</div>

{% include base_path %}

<div class="portfolio-grid">
  {% assign sorted_portfolio = site.portfolio | sort: "order" %}
  
  {% if sorted_portfolio.size > 0 %}
    {% for post in sorted_portfolio %}
      <div class="portfolio-card">
        {% if post.image %}
          <img src="{{ post.image | relative_url }}" alt="{{ post.title }} thumbnail">
        {% else %}
          <div class="placeholder-img">Image Placeholder</div>
        {% endif %}
        {% if post.caption %}
          <figcaption>{{ post.caption }}</figcaption>
        {% endif %}
        
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        {% if post.excerpt %}
          <p>{{ post.excerpt }}</p>
        {% else %}
          <p>Project description coming soon...</p>
        {% endif %}
      </div>
    {% endfor %}
  {% else %}
    <!-- Placeholder cards while portfolio is empty -->
    {% for i in (1..6) %}
      <div class="portfolio-card">
        <div class="placeholder-img">Image Placeholder</div>
        <h3>Project Title</h3>
        <p>Project description coming soon...</p>
      </div>
    {% endfor %}
  {% endif %}
</div>
