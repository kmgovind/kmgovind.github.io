---
layout: page
title: Physics-Informed Neural Network-Based Persistent Optimal Control of Sustainably Powered Mobile Robots
description: Using PINNs to learn infinite-horizon value functions
img: assets/img/publication_preview/IVE_Diagram.jpg
importance: 2
category: research
related_publications: false
---

## Explore the Learned Value Function

This interactive visualization is an early look at our ongoing work on physics-informed neural networks for persistent robot control. It shows the network's predicted discounted value as a function of robot position and battery state, for different information states.

Rotate the surface by dragging, hover to inspect values, and choose a clarity preset. To explore a custom information state, adjust the clarity values at the points of interest and select **Update surface**. These are predictions from a research model in development.

<p class="my-3">
  <a class="btn btn-primary" href="{{ '/assets/visualizations/pinn_ive/case1_value_surface.html' | relative_url }}" target="_blank" rel="noopener noreferrer">Open interactive visualization in a new tab ↗</a>
</p>

<iframe
  src="{{ '/assets/visualizations/pinn_ive/case1_value_surface.html' | relative_url }}"
  title="Interactive PINN value function: explore position, battery state, and clarity"
  loading="lazy"
  allow="fullscreen"
  style="display: block; width: 100%; height: 780px; height: clamp(620px, 85vh, 960px); border: 1px solid #b8c8d5; border-radius: 8px; background: #fff;">
</iframe>
<p class="caption text-center">For a larger workspace, use the new-tab link above. Custom clarity values are evaluated locally in your browser.</p>
