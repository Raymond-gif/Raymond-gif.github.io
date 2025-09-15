---
layout: splash
title: "Portfolio"
permalink: /portfolio/
header:
---

<!-- Hero Section -->
<div class="hero" style="
    position: relative;
    text-align: center;
    padding: 6rem 2rem;
    color: #fff;
    background: url('/images/engineeringheroimage.jpg') no-repeat center center;
    background-size: cover;
">
  <div style="
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.55);
      z-index: 1;
  "></div>
  <div style="position: relative; z-index: 2; max-width: 800px; margin: 0 auto;">
    <h1 style="
        font-size: 3.5rem; 
        margin-bottom: 1rem; 
        font-weight: 900; 
        text-shadow: 2px 2px 8px rgba(0,0,0,0.7);
    ">
      Portfolio
    </h1>
    <p style="
        font-size: 1.5rem; 
        margin-bottom: 2rem; 
        text-shadow: 1px 1px 6px rgba(0,0,0,0.6);
    ">
      A showcase of my personal, professional, and creative projects.
    </p>
    <a href="#projects" style="
        display: inline-block;
        padding: 0.75rem 2rem;
        background-color: #0055a5;
        color: #fff;
        border-radius: 8px;
        text-decoration: none;
        font-weight: bold;
        transition: background-color 0.3s ease, transform 0.3s ease;
    " onmouseover="this.style.backgroundColor='#003f7f'; this.style.transform='scale(1.05)'" 
       onmouseout="this.style.backgroundColor='#0055a5'; this.style.transform='scale(1)'">
      Explore Projects
    </a>
  </div>
</div>

<section id="projects" style="display:grid; grid-template-columns:repeat(auto-fit, minmax(300px, 1fr)); gap:2rem; padding:4rem 2rem;">
  {% assign sorted_portfolio = site.portfolio | sort: "order" %}
  {% if sorted_portfolio.size > 0 %}
    {% for post in sorted_portfolio %}
    <div class="project-card" style="background:#f7f7f7; border-radius:12px; overflow:hidden; box-shadow:0 4px 12px rgba(0,0,0,0.1); transition:transform 0.25s, box-shadow 0.25s;">
      {% if post.image %}
      <a href="{{ post.url | relative_url }}">
        <img src="{{ post.image | relative_url }}" alt="{{ post.title }} thumbnail" style="width:100%; height:200px; object-fit:cover;">
      </a>
      {% if post.caption %}
      <div class="project-caption">
        {{ post.caption }}
      </div>
      {% endif %}
      {% endif %}
      <div style="padding:1rem;">
        <h3 style="margin-bottom:0.5rem;">
          <a href="{{ post.url | relative_url }}" style="text-decoration:none; color:#222;">{{ post.title }}</a>
        </h3>
        <p style="font-size:0.95rem; color:#555;">
          {% if post.excerpt %}
            {{ post.excerpt }}
          {% else %}
            Project description coming soon...
          {% endif %}
        </p>
        <a href="{{ post.url | relative_url }}" class="read-more-btn" style="display:inline-block; margin-top:1rem; padding:0.5rem 1rem; background:#0055a5; color:#fff; border-radius:6px; text-decoration:none; font-weight:bold; transition:background 0.25s;">
          View Project →
        </a>
      </div>
    </div>
    {% endfor %}
  {% else %}
    {% for i in (1..6) %}
    <div class="project-card" style="background:#f7f7f7; border-radius:12px; overflow:hidden; box-shadow:0 4px 12px rgba(0,0,0,0.1); transition:transform 0.25s, box-shadow 0.25s;">
      <div style="width:100%; height:200px; background:#ddd; display:flex; align-items:center; justify-content:center; color:#666; font-size:1rem;">Image Placeholder</div>
      <div style="padding:1rem;">
        <h3 style="margin-bottom:0.5rem;">Project Title</h3>
        <p style="font-size:0.95rem; color:#555;">Project description coming soon...</p>
      </div>
    </div>
    {% endfor %}
  {% endif %}
</section>

<style>
  .project-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
  }
  .read-more-btn:hover {
    background: #003f7d;
  }
  .project-caption {
    font-size: 0.82rem;
    color: #888;
    background: #f5f5f5;
    margin: 0.3rem 1rem 0.5rem 1rem;
    padding: 0.18rem 0.6rem;
    border-radius: 4px;
    text-align: left;
    font-style: normal;
    letter-spacing: 0;
    box-shadow: none;
    border: none;
    line-height: 1.3;
  }
</style>

<!-- Footer CTA -->
<div style="text-align:center; padding:4rem 2rem; background:#f0f0f0;">
  <p style="font-size:1.1rem; margin-bottom:1rem;">Interested in working together or want to learn more about my projects?</p>
  <p style="font-size:1rem; margin:0.25rem 0;">Email: raymonddunn25@gmail.com,  rdunn1@uci.edu </p>
  <p style="font-size:1rem; margin:0.25rem 0;">LinkedIn: <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="color:#0a66c2; text-decoration:none;">linkedin.com/in/raymond-dunn-b13362200</a></p>
  <div style="display:flex; justify-content:center; gap:1rem; flex-wrap:wrap; margin-top:1rem;">
    <a href="mailto: raymonddunn25@gmail.com" style="padding:0.75rem 1.5rem; background-color:#0055a5; color:#fff; border-radius:8px; text-decoration:none; font-weight:bold;">Email Me</a>
    <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="padding:0.75rem 1.5rem; background-color:#0a66c2; color:#fff; border-radius:8px; text-decoration:none; font-weight:bold;">LinkedIn</a>
  </div>
</div>