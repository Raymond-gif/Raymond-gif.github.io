---
layout: splash
title: "Portfolio"
permalink: /portfolio/
---

<section class="rd-hero rd-hero--portfolio">
  <div class="rd-hero__content">
    <h1>Portfolio</h1>
    <p>A showcase of my engineering projects, coding work, and creative problem-solving.</p>
  </div>
</section>

<section id="projects" class="rd-project-grid" aria-label="Portfolio projects">
  {% assign sorted_projects = site.portfolio | sort: "order" %}
  {% for project in sorted_projects %}
  <article class="rd-project-card">
    {% if project.image %}
    <a href="{{ project.url }}">
      <img src="{{ project.image }}" alt="{{ project.title }}">
    </a>
    {% if project.caption %}
    <p class="rd-project-card__caption">{{ project.caption }}</p>
    {% endif %}
    {% endif %}
    <div class="rd-project-card__body">
      <h2><a href="{{ project.url }}">{{ project.title }}</a></h2>
      <p>{{ project.excerpt }}</p>
      <a href="{{ project.url }}" class="rd-read-more">Read More <i class="fas fa-arrow-right" aria-hidden="true"></i></a>
    </div>
  </article>
  {% endfor %}
</section>
