---
layout: page
title: news and updates
permalink: /news/
description: Research news, talks, milestones, and updates over time.
nav: false
---

[← Back to Highlights]({{ '/highlights/' | relative_url }})

{% assign news_items = site.news | where_exp: 'item', 'item.published != false' | sort: 'date' | reverse %}
{% assign current_year = '' %}
{% for item in news_items %}
{% assign item_year = item.date | date: '%Y' %}
{% if item_year != current_year %}

<h2>{{ item_year }}</h2>
{% assign current_year = item_year %}
{% endif %}
{% include news_item.liquid item=item %}
{% endfor %}
