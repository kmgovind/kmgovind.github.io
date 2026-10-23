---
layout: page
title: "Stochastic Gatekeeper: Online Safety Verification"
description: "Sampling-based safety verification for nonlinear robots operating under uncertain disturbances."
img: assets/img/coursework/aerosp740/safety-simulation.png
importance: 1
category: coursework
related_publications: false
---

**AEROSP 740 · University of Michigan · Team project**

A robot's mission controller may know how to reach a goal without knowing whether its next move is safe. In this project, we developed a stochastic extension of the gatekeeper framework that checks proposed behavior online and switches to a backup controller when needed.

The goal was to handle nonlinear dynamics and uncertain disturbances while preserving as much of the mission controller's behavior as possible.

## Checking Safety Before Committing

The method evaluates candidate times at which the robot could switch from its nominal controller to a backup controller. For each candidate, it samples disturbance sequences and rolls out the resulting trajectories. A candidate passes only if every sampled trajectory stays within the known safe region and reaches the backup set.

The algorithm selects the latest passing switching time. If no new candidate passes, it retains the previously committed switching time. JAX parallelization allows the sampled rollouts to be evaluated together.

Our statistical analysis relates the number of samples to a chosen safety tolerance and the confidence of the verification step. The guarantee depends on the disturbance model, independent sampling, and an appropriate invariant backup set; it is not an unconditional guarantee against every possible disturbance.

## Simulation: Navigating Uncertain Terrain

We evaluated the method on a kinematic bicycle model navigating around obstacles. Friction, steering slip, and process noise vary with the robot's state and location, creating regions with different levels of uncertainty. The nominal controller steers toward the goal, while the backup controller brakes and turns left until the robot stops.

<figure class="my-4">
  <img src="{{ '/assets/img/coursework/aerosp740/safety-simulation.png' | relative_url }}" alt="Six simulation panels show a robot navigating obstacles, distance to goal, controller selection, acceleration, steering, and velocity." class="img-fluid rounded z-depth-1" loading="lazy" style="width: 100%;">
  <figcaption class="caption text-center">The robot approaches the goal while switching between mission execution and backup braking near obstacles. Colored terrain regions represent different friction conditions.</figcaption>
</figure>

## Safety Versus Conservatism

The report compares 100 simulations for each sample count:

| Outcome                      | 100 samples | 10,000 samples |
| :--------------------------- | ----------: | -------------: |
| Reached the goal safely      |         74% |            84% |
| Remained safe but deadlocked |          2% |            16% |
| Unsafe                       |         24% |             0% |

More samples reduced observed unsafe outcomes, but also made the controller more conservative: some runs stopped safely without completing the mission. The absence of unsafe outcomes in the larger-sample experiment is an empirical result from these trials, rather than proof of zero collision probability.

The main lesson is that safety verification must be evaluated alongside task completion. Rejecting risky motion can protect the robot while still leaving a planning problem to solve.

## Team and Code

Developed with **Daniel Cherenson, Joon Lee, Samit Mohapatra, and Marshall Vielmetti**.

[View the project code](https://github.com/joonlee16/stochastic_gatekeeper).
