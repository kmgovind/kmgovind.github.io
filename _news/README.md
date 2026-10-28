# Adding a news update

Create one Markdown file in this folder for each update, for example:
`2026-11-01-a-short-title.md`.

```markdown
---
title: "A short, descriptive headline"
date: 2026-11-01
teaser: "One or two sentences for Highlights and the homepage."
---

Write the full update here using Markdown. You can add images, links,
and other supporting content.
```

The date controls chronological order. The five latest published updates appear
on Highlights, the three latest appear on the homepage, and all appear at
`/news/`, grouped by year. Each update also gets its own page.

- Set `published: false` to keep a draft out of the site.
- Use `permalink: /news/your-chosen-slug/` if you want an explicit permanent URL.
- Optional `video_id` embeds a YouTube recording on the full update page.
- Optional `event_url` adds an event-details link.
- Optional `links` adds related-work links:

```yaml
links:
  - label: Project overview
    url: /projects/periodic_ive/
```

You can change `news_limit` in `_pages/repositories.md` to 3, 4, or 5.
The homepage limit is in `_pages/about.md` under `recent_updates`.
Add repository highlights in `_data/highlights.yml`; news belongs here.

The old `announcement_*.md` files are unpublished theme samples.
This README is excluded from the website build.
