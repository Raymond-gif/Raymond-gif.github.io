---
layout: splash
title: "Academic Works"
permalink: /academics/
---

<!-- Hero Section -->
<div class="hero" style="
    position: relative;
    text-align: center;
    padding: 6rem 2rem;
    color: #fff;
    background: url('/images/fluidheader.jpg') no-repeat center center;
    background-size: cover;
">
  <!-- Stronger overlay for better readability -->
  <div style="
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.55); /* increased from 0.35 to 0.55 */
      z-index: 1;
  "></div>

  <!-- Hero content -->
  <div style="position: relative; z-index: 2; max-width: 800px; margin: 0 auto;">
    <h1 style="
        font-size: 3.5rem; 
        margin-bottom: 1rem; 
        font-weight: 900; 
        text-shadow: 2px 2px 8px rgba(0,0,0,0.7);
    ">
      Academic Works
    </h1>
    <p style="
        font-size: 1.5rem; 
        margin-bottom: 2rem; 
        text-shadow: 1px 1px 6px rgba(0,0,0,0.6);
    ">
      A curated collection of my research projects, publications, and academic contributions in fluid mechanics and applied mathematics.
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
  {% assign sorted_works = site.academics | sort: "order" %}
  {% for work in sorted_works %}
  <div class="project-card" style="background:#f7f7f7; border-radius:12px; overflow:hidden; box-shadow:0 4px 12px rgba(0,0,0,0.1); transition:transform 0.25s, box-shadow 0.25s;">
    {% if work.image %}
    <a href="{{ work.url }}">
      <img src="{{ work.image }}" alt="{{ work.title }}" style="width:100%; height:200px; object-fit:cover;">
    </a>
    {% if work.caption %}
    <div class="project-caption">
      {{ work.caption }}
    </div>
    {% endif %}
    {% endif %}
    <div style="padding:1rem;">
      <h3 style="margin-bottom:0.5rem;">
        <a href="{{ work.url }}" style="text-decoration:none; color:#222;">{{ work.title }}</a>
      </h3>
      <p style="font-size:0.95rem; color:#555;">{{ work.excerpt }}</p>
      <a href="{{ work.url }}" class="read-more-btn" style="display:inline-block; margin-top:1rem; padding:0.5rem 1rem; background:#0055a5; color:#fff; border-radius:6px; text-decoration:none; font-weight:bold; transition:background 0.25s;">
        Read More →
      </a>
    </div>
  </div>
  {% endfor %}
</section>

<style>
  /* Card hover effect */
  .project-card:hover {
    transform: translateY(-6px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
  }

  /* Button hover effect */
  .read-more-btn:hover {
    background: #003f7d; /* darker shade */
  }

  /* Subtle, inconspicuous caption styling */
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
  <p style="font-size:1.1rem; margin-bottom:1rem;">Interested in collaborating or learning more about my work?</p>
  
  <!-- Contact info -->
  <p style="font-size:1rem; margin:0.25rem 0;">Email: raymonddunn25@gmail.com,  rdunn1@uci.edu </p>
  <p style="font-size:1rem; margin:0.25rem 0;">LinkedIn: <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="color:#0a66c2; text-decoration:none;">linkedin.com/in/raymond-dunn-b13362200</a></p>
  
  <!-- Optional button links -->
  <div style="display:flex; justify-content:center; gap:1rem; flex-wrap:wrap; margin-top:1rem;">
    <a href="mailto: raymonddunn25@gmail.com" style="padding:0.75rem 1.5rem; background-color:#0055a5; color:#fff; border-radius:8px; text-decoration:none; font-weight:bold;">Email Me</a>
    <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="padding:0.75rem 1.5rem; background-color:#0a66c2; color:#fff; border-radius:8px; text-decoration:none; font-weight:bold;">LinkedIn</a>
  </div>
</div>

<style>
.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0,0,0,0.15);
}
</style>

