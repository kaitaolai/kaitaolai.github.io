---
layout: page
permalink: /repositories/
title: repositories
description: Open-source code on GitHub.
nav: true
nav_order: 4
---

<div class="row row-cols-1 row-cols-md-2">
{% for repo in site.data.repo_cards %}
  <div class="col mb-4">
    <div class="card h-100 hoverable">
      <a href="{{ repo.url }}" target="_blank" rel="noopener">
        {% if repo.fit == "banner" %}{% assign st = "width: 100%; height: auto;" %}{% elsif repo.fit == "contain" %}{% assign st = "object-fit: contain; height: 220px; background: #fff;" %}{% else %}{% assign st = "object-fit: cover; height: 220px;" %}{% endif %}
        <img src="{{ repo.image | relative_url }}" class="card-img-top" alt="{{ repo.name }}" style="{{ st }}">
      </a>
      <div class="card-body">
        <h2 class="card-title" style="font-size: 1.3rem;"><a href="{{ repo.url }}" target="_blank" rel="noopener">{{ repo.name }}</a></h2>
        <p class="card-text">{{ repo.description }}</p>
        <p class="card-text"><small class="text-muted">{% if repo.language %}{{ repo.language }} · {% endif %}<a href="{{ repo.url }}" target="_blank" rel="noopener"><i class="fa-brands fa-github"></i> GitHub</a>{% if repo.homepage %} · <a href="{{ repo.homepage }}" target="_blank" rel="noopener">website</a>{% endif %}</small></p>
      </div>
    </div>
  </div>
{% endfor %}
</div>

All repositories: [github.com/taowis](https://github.com/taowis).
