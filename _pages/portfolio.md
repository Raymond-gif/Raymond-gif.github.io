---
layout: splash
title: "Portfolio"
permalink: /portfolio/
---

<section class="rd-hero rd-hero--portfolio">
  <div class="rd-hero__content">
    <h1>Portfolio</h1>
    <p>A showcase of my engineering projects, coding work, and creative problem-solving.</p>
    <div class="rd-hero__actions">
      <a class="rd-btn" href="#projects">Explore Projects</a>
      <a class="rd-btn rd-btn--secondary" href="/academics/">Academic Works</a>
    </div>
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
      <a href="{{ project.url }}" class="rd-read-more">Read More -></a>
    </div>
  </article>
  {% endfor %}
</section>

<section class="rd-contact-cta">
  <p>Want to discuss a project or collaborate?</p>
  <div class="rd-contact-cta__links">
    <a class="rd-btn" href="mailto:raymonddunn25@gmail.com">Email Me</a>
    <a class="rd-btn rd-btn--linkedin" href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" rel="noopener">LinkedIn</a>
  </div>
  <p class="rd-contact-cta__meta">raymonddunn25@gmail.com</p>
  <p class="rd-contact-cta__meta"><a href="https://www.linkedin.com/in/raymond-dunn-b13362200" target="_blank" rel="noopener">linkedin.com/in/raymond-dunn-b13362200</a></p>
</section>
