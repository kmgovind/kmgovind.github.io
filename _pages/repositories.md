---
layout: page
permalink: /highlights/
title: highlights
description: Research news, talks, and selected code from my work in robotics and control.
nav: true
nav_order: 4
news_limit: 5
---

News and code from my research. Visit [Projects]({{ '/projects/' | relative_url }}) for detailed project write-ups.

[News](#news) · [Repos](#repos)

## News

{% assign news_items = site.news | where_exp: 'item', 'item.published != false' | sort: 'date' | reverse %}
{% assign news_limit = page.news_limit | default: 5 %}
{% for item in news_items limit: news_limit %}
{% include news_item.liquid item=item %}
{% endfor %}

<p><a href="{{ '/news/' | relative_url }}">View all news and updates →</a></p>

---

## Repos

These repositories connect the ideas in my papers and project pages to their implementations. Some are individual projects; others are collaborations.

<div class="row">
  {% for item in site.data.highlights.code %}
    <div class="col-md-6 mb-4">
      <article class="card h-100">
        <div class="card-body d-flex flex-column">
          {% if item.context %}<p class="small text-muted mb-2">{{ item.context | escape }}</p>{% endif %}
          <h3 class="h5 card-title">{{ item.title | escape }}</h3>
          <p class="card-text">{{ item.description | escape }}</p>
          <p class="small text-muted">{{ item.repository | escape }}</p>
          <p class="mt-auto mb-0">
            <a href="https://github.com/{{ item.repository }}" target="_blank" rel="noopener noreferrer">Explore code ↗</a>
            · <a href="https://github.com/{{ item.repository }}#readme" target="_blank" rel="noopener noreferrer">Start with the README</a>
            {% if item.project_url %}
              · <a href="{{ item.project_url | relative_url }}">Project overview</a>
            {% endif %}
            {% if item.paper_url %}
              · <a href="{{ item.paper_url | relative_url }}">Paper</a>
            {% endif %}
          </p>
        </div>
      </article>
    </div>
  {% endfor %}
</div>

[More code on GitHub](https://github.com/kmgovind?tab=repositories) · [All project pages]({{ '/projects/' | relative_url }}) · [Publications]({{ '/publications/' | relative_url }})
