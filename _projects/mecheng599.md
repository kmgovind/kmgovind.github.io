---
layout: page
title: "Path Planning for Wave-Powered Desalination"
description: "Comparing genetic algorithms and reinforcement learning for a mobile wave-powered freshwater system."
img: assets/img/coursework/mecheng599/ga-route.png
importance: 2
category: coursework
related_publications: false
---

**MECHENG 599 · University of Michigan · Team project**

A mobile desalination system can seek out productive waves instead of remaining at a fixed location. However, traveling to a better resource takes time, and the same sea state affects both vehicle motion and freshwater production.

This project compared two data-driven planning methods for the **WEC-Mobile**, a wave-powered mobile desalination concept. The objective was to fill an onboard freshwater tank and return to the starting location in minimum time.

## A Planner Inside a Planner

We used a nested approach. An outer planner proposes a route through a sequence of waypoints, while an inner optimization determines the effective speed profile along that route. This separates the difficult spatial search from a speed-allocation problem with a more structured switching solution.

For the outer planner, we compared:

- **Genetic algorithm (GA):** Evolves candidate waypoint sequences through selection, crossover, and mutation.
- **Reinforcement learning (RL):** Uses proximal policy optimization to learn directional decisions from interaction with the simulated environment.

The simulations use spatially varying wave conditions derived from buoy data. For the reported comparison, the environment is held fixed in time, and the mission follows an out-and-back structure.

## Routes Through the Wave Resource

<figure class="my-4">
  <img src="{{ '/assets/img/coursework/mecheng599/ga-route.png' | relative_url }}" alt="Genetic-algorithm route over a map of spatially varying desalination rates in liters per hour." class="img-fluid rounded z-depth-1" loading="lazy" style="width: 100%;">
  <figcaption class="caption text-center">The GA route moves toward a region with higher freshwater production. The background shows the desalination rate associated with the local wave resource.</figcaption>
</figure>

<figure class="my-4">
  <img src="{{ '/assets/img/coursework/mecheng599/rl-route.png' | relative_url }}" alt="Reinforcement-learning route over the same desalination-rate map." class="img-fluid rounded z-depth-1" loading="lazy" style="width: 100%;">
  <figcaption class="caption text-center">The RL planner produces a different route through the same environment, allowing the two approaches to be compared under a common resource map.</figcaption>
</figure>

## What the Comparison Showed

| Reported measure                       | Genetic algorithm | Reinforcement learning |
| :------------------------------------- | ----------------: | ---------------------: |
| Mission time                           |           20.46 h |                22.94 h |
| Average desalination rate              |          4.91 L/h |               4.38 L/h |
| Distance traveled                      |         111.79 km |              150.73 km |
| Average steady-state speed             |          1.52 m/s |               1.83 m/s |
| Approximate optimization/training time |             7 min |                    4 h |

The GA completed the mission sooner despite its lower average speed. This illustrates why route quality and resource allocation matter alongside how quickly a vehicle travels.

In this spatially varying, temporally static test, the GA also required substantially less computation than RL. These timings describe the reported implementations and training runs; they are not general performance guarantees for either method.

## What Comes Next

The comparison does not establish how the methods perform when the wave field changes over time. Extending the planner to changing forecasts, uncertain resources, and replanning during a mission would be important next steps. The results shown here are simulations, rather than a field deployment of the planning methods.

## Team and Code

Developed with **Minhazul Alam, Xiangyu Lu, and Zihan Yu**.

[View the project code](https://github.com/kmgovind/ME599_Final_WEC_Mobile).
