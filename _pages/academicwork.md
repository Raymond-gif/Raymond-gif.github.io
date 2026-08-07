---
layout: splash
title: "Academic Works"
permalink: /academics/
---

<section class="rd-hero rd-hero--academics rd-hero--academic-index">
  <div class="rd-hero__content">
    <h1>Academic Works</h1>
    <p>A curated collection of research projects, notes, and academic work in fluid mechanics and applied mathematics.</p>
    <div class="rd-hero__actions">
      <a class="rd-btn" href="#projects">Explore Projects</a>
    </div>
  </div>
</section>

<section id="projects" class="rd-project-grid rd-project-grid--academic" aria-label="Academic projects">
  {% assign sorted_works = site.academics | sort: "order" %}
  {% for work in sorted_works %}
  <article class="rd-project-card rd-project-card--academic{% unless work.image %} rd-project-card--no-media{% endunless %}">
    {% if work.image %}
    <div class="rd-project-card__media">
      <a href="{{ work.url }}">
        <img src="{{ work.image }}" alt="{{ work.title }}">
      </a>
      {% if work.caption %}
      <p class="rd-project-card__caption">{{ work.caption }}</p>
      {% endif %}
    </div>
    {% endif %}
    <div class="rd-project-card__body">
      <h2><a href="{{ work.url }}">{{ work.title }}</a></h2>
      {% unless work.hide_excerpt %}
      <p>{{ work.excerpt }}</p>
      {% endunless %}
      <a href="{{ work.url }}" class="rd-read-more">Read More -></a>
    </div>
  </article>
  {% endfor %}
</section>
