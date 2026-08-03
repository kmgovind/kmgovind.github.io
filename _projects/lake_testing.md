---
layout: page
title: Clarity-Driven Adaptive Mission Planning for a Solar-Powered Autonomous Surface Vessel
description: An energy-aware ergodic search framework that optimizes trajectory and speed using a mathematically grounded information metric (clarity) for long-duration marine missions.
img: assets/img/publication_preview/2025-lake-testing.jpg
importance: 1
category: research
related_publications: false
---

# Abstract

Sustainably powered mobile robots enable long-duration observational missions by harvesting energy from the environment. However, effective autonomy requires these platforms to adaptively allocate limited energy to maximize information gathering quality over time. In this paper, we present an integrated, energy-aware, clarity-driven adaptive mission planning framework for a solar-powered Autonomous Surface Vessel (ASV). We define _clarity_—a statistically rigorous information metric derived from differential entropy—to capture spatial certainty gain alongside continuous temporal decay at unvisited locations. Using a Spatiotemporal Gaussian Process Kalman Filter (STGPKF), the vessel dynamically updates an estimated scientific field and continuously adapts a target clarity map from in-situ measurements. An ergodic path planner then optimizes spatial visitation trajectories while an energy controller adjusts vessel speed based on tightened state-of-charge (SOC) constraints and solar irradiance models. We validate this complete framework through both numerical simulations and real-world field experiments on a SeaTrac SP-48 ASV at Jordan Lake, North Carolina, demonstrating that the vehicle actively targets regions of high scientific interest while maintaining energy feasibility.

<div class="embed-responsive embed-responsive-16by9 my-4" style="width: 100%;">
  <iframe 
    class="embed-responsive-item rounded z-depth-1" 
    src="https://www.youtube.com/embed/hslDizSCT2s?si=8vWFRnQB0t0_AFac" 
    title="Experiment Preview" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
    referrerpolicy="strict-origin-when-cross-origin" 
    allowfullscreen>
  </iframe>
</div>
<div class="caption text-center">
    Experiment preview showing clarity-driven trajectory optimization in action at Jordan Lake, NC.
</div>

---

## Key Contributions

- **Unified Energy-Information Framework:** The first energy-aware adaptive ergodic search control framework that couples a statistically rigorous metric for information decay (_clarity_) with explicit state-of-charge (SOC) power dynamics.
- **Real-Time Science-Aware Adaptation:** An STGPKF-based pipeline that dynamically transforms raw field data into zero-mean Gaussian models, updates target distributions online, and focuses search efforts on high-value regions (e.g., regions near a target rated wind speed).
- **Optimal Speed and Ergodic Control:** Integrates tightened SOC constraints to derive optimal speed profiles, coupled with a projection-based ergodic trajectory planner for continuous spatial exploration.
- **Experimental Validation:** Fully implemented and validated via field tests using the SeaTrac SP-48 ASV on Jordan Lake, NC.

---

## Methodological Overview

<img src="/assets/img/tcst_horizontal_block_diagram.png" alt="Control Block Diagram" class="img-fluid rounded z-depth-1" style="width: 100%; height: auto; margin: 1rem 0;">

1. **Information Metric (_Clarity_):** $q(p,t) \in [0,1]$ quantifies certainty across spatial locations $p$ over time $t$. Clarity evolves via a first-order differential equation balancing information gain from measurements and temporal decay:
   $$\dot{q}(p,t) = S(p_r(t),p)\left(1-q(p,t)\right)^2 - D\left(p,q(p,t)\right)$$
2. **Energy & Speed Planning:** Power dynamics account for solar irradiance $P_{in}(t)$, hotel loads $k_h$, motor power draw $k_m u(t)^3$, and battery constraints $b_{min} \le b(t) \le b_{max}$. Tightened constraint functions ensure point-wise feasibility across varying solar conditions.
3. **Ergodic Path Generation:** Minimizes the spectral discrepancy between time-averaged vehicle trajectories and the dynamically generated target spatial distribution (TSD).

---

## Results at a Glance

### Simulation Studies

In spatiotemporally varying synthetic environments, the proposed clarity-driven ergodic strategy consistently concentrated sampling effort near target scientific values, outperforming non-adaptive lawnmower (line transect) benchmarks.

| Strategy                   | Mean Measurement Error $\overline{x}$ | Standard Deviation $\sigma$ |
| :------------------------- | :-----------------------------------: | :-------------------------: |
| **Clarity-Driven Ergodic** |       **$-0.710 \text{ m/s}$**        |   **$1.158 \text{ m/s}$**   |
| Line Transect              |         $-1.555 \text{ m/s}$          |     $1.099 \text{ m/s}$     |

<div style="margin-top: 1.5rem;"></div>

### Field Experiments (Jordan Lake, NC)

Field deployments on the **SeaTrac SP-48 ASV** confirmed that closed-loop SOC speed control maintains energy balance while the ergodic planner dynamically steers the vessel to spend more time in high-value regions.

| Mission Profile             | Strategy | Mean Deviation from Target Speed | Standard Deviation  |
| :-------------------------- | :------- | :------------------------------: | :-----------------: |
| **90 min (Fixed Speed)**    | Ergodic  |     **$0.081 \text{ m/s}$**      | $2.146 \text{ m/s}$ |
|                             | Transect |       $0.533 \text{ m/s}$        | $2.052 \text{ m/s}$ |
| **90 min (Variable Speed)** | Ergodic  |     **$-0.894 \text{ m/s}$**     | $1.595 \text{ m/s}$ |
|                             | Transect |       $1.176 \text{ m/s}$        | $2.183 \text{ m/s}$ |
| **3 hour (Variable Speed)** | Ergodic  |     **$0.048 \text{ m/s}$**      | $2.008 \text{ m/s}$ |
|                             | Transect |       $0.846 \text{ m/s}$        | $2.642 \text{ m/s}$ |

---

## Read the Full Paper

For complete mathematical formulations of clarity, control law derivations, and detailed analysis of long-horizon persistent planning, please refer to our publication.
