---
layout: splash
title: "Academic Works"
permalink: /academics/
---

<section class="rd-hero rd-hero--academics rd-hero--academic-index">
  <div class="rd-hero__content">
    <h1>Academic Works</h1>
    <p>A curated collection of research projects, notes, and academic work in fluid mechanics and applied mathematics.</p>
  </div>
</section>

<div class="rd-project-filter">
  <label for="academic-work-filter">Filter academic work</label>
  <div class="rd-project-filter__control">
    <i class="fas fa-search" aria-hidden="true"></i>
    <input id="academic-work-filter" type="search" placeholder="Search titles and topics" autocomplete="off" data-project-filter>
  </div>
  <p class="rd-project-filter__empty" data-project-filter-empty hidden>No matching academic work.</p>
</div>

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
      <a href="{{ work.url }}" class="rd-read-more">Read More <i class="fas fa-arrow-right" aria-hidden="true"></i></a>
    </div>
  </article>
  {% endfor %}
</section>
