---
layout: splash
title: "Portfolio"
permalink: /portfolio/
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
  <!-- Dark overlay for readability -->
  <div style="
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.55);
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
      My Portfolio
    </h1>
    <p style="
        font-size: 1.5rem; 
        margin-bottom: 2rem; 
        text-shadow: 1px 1px 6px rgba(0,0,0,0.6);
    ">
      A showcase of my engineering projects, coding work, and creative problem-solving.
    </p>

    <!-- CTA buttons -->
    <div style="margin-top: 2rem; display:flex; justify-content:center; flex-wrap:wrap; gap:1rem;">
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

      <a href="/academics/" style="
          display: inline-block;
          padding: 0.75rem 2rem;
          background-color: #fff;
          color: #0055a5;
          border: 2px solid #0055a5;
          border-radius: 8px;
          text-decoration: none;
          font-weight: bold;
          transition: background-color 0.3s ease, color 0.3s ease, transform 0.3s ease;
      " onmouseover="this.style.backgroundColor='#f0f0f0'; this.style.transform='scale(1.05)'" 
         onmouseout="this.style.backgroundColor='#fff'; this.style.transform='scale(1)'">
        Academic Works
      </a>
    </div>
  </div>
</div>

<!-- Project Grid -->
<section id="portfolio" style="display:grid; grid-template-columns:repeat(auto-fit, minmax(300px, 1fr)); gap:2rem; padding:4rem 2rem;">
  {% assign sorted_projects = site.portfolio | sort: "order" %}
  {% for project in sorted_projects %}
  <div class="project-card" style="background:#f7f7f7; border-radius:12px; overflow:hidden; box-shadow:0 4px 12px rgba(0,0,0,0.1); transition:transform 0.25s, box-shadow 0.25s;">
    {% if project.image %}
    <a href="{{ project.url }}">
      <img src="{{ project.image }}" alt="{{ project.title }}" style="width:100%; height:200px; object-fit:cover;">
    </a>
    {% if project.caption %}
    <div class="project-caption">
      {{ project.caption }}
    </div>
    {% endif %}
    {% endif %}
    <div style="padding:1rem;">
      <h3 style="margin-bottom:0.5rem;">
        <a href="{{ project.url }}" style="text-decoration:none; color:#222;">{{ project.title }}</a>
      </h3>
      <p style="font-size:0.95rem; color:#555;">{{ project.excerpt }}</p>
      <a href="{{ project.url }}" class="read-more-btn" style="
          display:inline-block;
          margin-top:1rem;
          padding:0.5rem 1rem;
          background:#0055a5;
          color:#fff;
          border-radius:6px;
          text-decoration:none;
          font-weight:bold;
          transition: background 0.25s ease, transform 0.25s ease;
      " 
      onmouseover="this.style.backgroundColor='#003f7d'; this.style.transform='scale(1.05)'" 
      onmouseout="this.style.backgroundColor='#0055a5'; this.style.transform='scale(1)'">
        Read More →
      </a>
    </div>
  </div>
  {% endfor %}
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
    line-height: 1.3;
  }
</style>

<!-- Footer CTA -->
<div style="text-align:center; padding:4rem 2rem; background:#f0f0f0;">
  <p style="font-size:1.1rem; margin-bottom:1rem;">Want to discuss a project or collaborate?</p>
  
  <p style="font-size:1rem; margin:0.25rem 0;">Email: raymonddunn25@gmail.com</p>
  <p style="font-size:1rem; margin:0.25rem 0;">LinkedIn: <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="color:#0a66c2; text-decoration:none;">linkedin.com/in/raymond-dunn-b13362200</a></p>
  
  <div style="display:flex; justify-content:center; gap:1rem; flex-wrap:wrap; margin-top:1rem;">
    <a href="mailto:raymonddunn25@gmail.com" style="
        padding:0.75rem 1.5rem;
        background-color:#0055a5;
        color:#fff;
        border-radius:8px;
        text-decoration:none;
        font-weight:bold;
        transition: background-color 0.3s ease, transform 0.3s ease;
    " 
    onmouseover="this.style.backgroundColor='#003f7f'; this.style.transform='scale(1.05)'" 
    onmouseout="this.style.backgroundColor='#0055a5'; this.style.transform='scale(1)'">
      Email Me
    </a>
    <a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" style="
        padding:0.75rem 1.5rem;
        background-color:#0a66c2;
        color:#fff;
        border-radius:8px;
        text-decoration:none;
        font-weight:bold;
        transition: background-color 0.3s ease, transform 0.3s ease;
    " 
    onmouseover="this.style.backgroundColor='#005582'; this.style.transform='scale(1.05)'" 
    onmouseout="this.style.backgroundColor='#0a66c2'; this.style.transform='scale(1)'">
      LinkedIn
    </a>
  </div>
</div>
