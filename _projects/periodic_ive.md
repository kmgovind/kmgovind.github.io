---
layout: page
title: Optimally Trading Energy for Information through Speed Trajectory Optimization of Sustainably Powered Mobile Robots
description: Characterizing energy-information tradeoffs in a periodic optimal control setting
img: assets/img/publication_preview/2026_periodic_path.png
importance: 1
category: research
related_publications: false
---

**How should a solar-powered robot spend its energy to keep environmental information useful over time?**

Moving faster revisits locations sooner, but propulsion becomes increasingly expensive. Moving slowly provides more sensing time nearby, while information elsewhere becomes stale. This project studies how to balance those effects by optimizing the robot's speed along a repeated monitoring route.

In a Chesapeake Bay salinity simulation, adapting speed improves weighted clarity by **up to 59.5%** over constant-speed traversal under the same average power constraint.

## Turning Energy into Information

<figure class="my-4">
  <img src="{{ '/assets/img/periodic_ive/energy-information.png' | relative_url }}" alt="Solar energy fills an energy reservoir, which is converted through sensing into information that also decays over time." class="img-fluid rounded" loading="lazy" style="width: 100%;">
  <figcaption class="caption text-center">Speed regulates the conversion of harvested energy into information. SeaTrac SP-48 image credit: SeaTrac; reproduced from the paper.</figcaption>
</figure>

We model the robot as two coupled reservoirs: a physical battery and a virtual store of information. Information is measured using **clarity**, a normalized measure of certainty that increases with sensing and decays between observations.

The robot repeatedly traverses a fixed closed path. We optimize its speed to maximize time-averaged, importance-weighted clarity while respecting an average power budget. Requiring clarity to repeat from one lap to the next captures persistent operation. The lap duration is also determined by the optimization.

## Where Should the Robot Slow Down?

The resulting behavior is intuitive: allocate more sensing time to high-priority regions and move faster through lower-priority regions. The optimization determines how much to slow down and accelerate, accounting for sensing range, information decay, and propulsion cost.

<figure class="my-4">
  <img src="{{ '/assets/img/periodic_ive/speed-allocation.png' | relative_url }}" alt="Optimized speeds along a 100 meter route decrease around high-importance regions centered at 30 and 80 meters; curves compare three discretization resolutions." class="img-fluid rounded" loading="lazy" style="width: 100%;">
  <figcaption class="caption text-center">An illustrative 100 m route shows how spatial priorities shape speed. The shaded profile indicates importance; the curves show optimized speed at different numerical resolutions.</figcaption>
</figure>

The paper gives this behavior a theoretical foundation through Pontryagin's Maximum Principle and the **Information Value of Energy (IVE)** relationship between marginal propulsion power and the spatial and energy costates. Three useful consequences are:

- **Smooth speed allocation:** Under the stated regularity and strict energy-value assumptions, the unconstrained optimal speed is continuous and the Hamiltonian's pointwise speed maximizer is unique.
- **Constant speed for uniform priorities:** Equal importance weights yield constant speed in a uniform, shift-invariant environment.
- **Diminishing returns from faster revisits:** At increasingly high constant traversal speeds, time-averaged clarity approaches a finite saturation limit set by sensing intensity and information decay.

These results characterize necessary conditions and solution structure; they do not establish global optimality for the full nonlinear problem.

## Monitoring Salinity in Chesapeake Bay

The application uses NOAA Chesapeake Bay Operational Forecast System salinity fields along an approximately 150 km closed monitoring route. Over a five-day simulation, each completed lap updates the importance weights used to plan the next lap's speed.

<figure class="my-4">
  <video controls muted loop playsinline preload="none" poster="{{ '/assets/img/periodic_ive/chesapeake-salinity-poster.jpg' | relative_url }}" aria-label="Animation of simulated Chesapeake Bay surface salinity with the fixed monitoring route shown in red" style="display: block; width: 100%; max-width: 800px; margin: auto;">
    <source src="{{ '/assets/video/periodic_ive/chesapeake-salinity.mp4' | relative_url }}" type="video/mp4">
    Your browser does not support embedded video. <a href="{{ '/assets/video/periodic_ive/chesapeake-salinity.mp4' | relative_url }}">Download the salinity animation.</a>
  </video>
  <figcaption class="caption text-center">The changing salinity field and fixed monitoring route. This animation shows the simulated environment; the speed comparison below shows the planner's response.</figcaption>
</figure>

The simulated vehicle uses the SeaTrac SP-48 propulsion model with a **750 W average input power**. Priorities are defined relative to a **30 PSU salinity reference**: salinities above the reference receive full weight, while weights below it decrease with distance from the reference. The spread $\sigma_\zeta$ controls how selective this weighting is.

<figure class="my-4">
  <img src="{{ '/assets/img/periodic_ive/chesapeake-speed.png' | relative_url }}" alt="Five-day speed comparison for weighting spreads of 2, 3, and 4 PSU alongside the constant-speed baseline; more selective weighting produces larger speed changes and near-stationary intervals." class="img-fluid rounded" loading="lazy" style="width: 100%;">
  <figcaption class="caption text-center">More selective priorities produce stronger speed adaptation, including near-stationary sensing intervals. Broader weighting produces a profile closer to constant speed.</figcaption>
</figure>

### What Improves?

IVE increases weighted clarity by **59.5%, 19.6%, and 2.0%** for spreads of 2, 3, and 4 PSU, respectively. Each gain compares the two strategies under the same weighting function and power constraint. Changing the spread changes the monitoring objective, so clarity totals should be compared within each row.

At a spread of 3 PSU, the mean salinity deviation from the reference improves from −2.58 to −1.43 PSU, accompanied by a larger standard deviation. The benefit is therefore best understood as allocating observations according to the mission's priorities.

<details class="my-4">
<summary><strong>Full numerical results (Table I of the paper)</strong></summary>
<div class="table-responsive" markdown="1">

Paired values are **IVE / Constant Speed**. PSU denotes practical salinity units.

| $\sigma_\zeta$ | Clarity (IVE / Constant Speed) |  Gain | Mean deviation (PSU) | Std. dev. (PSU) |
| :------------: | -----------------------------: | ----: | -------------------: | --------------: |
|      2.0       |          44,528.41 / 27,911.94 | 59.5% |        −2.54 / −2.58 |     2.10 / 2.34 |
|      3.0       |          42,761.25 / 35,764.20 | 19.6% |        −1.43 / −2.58 |     3.03 / 2.34 |
|      4.0       |          42,234.46 / 41,404.75 |  2.0% |        −2.38 / −2.58 |     2.65 / 2.34 |

</div>
</details>

## Paper and Next Steps

**Kavin M. Govindarajan, Dimitra Panagou, and Chris Vermillion.** _Optimally Trading Energy for Information through Speed Trajectory Optimization of Sustainably Powered Mobile Robots._

See the [publication listing]({{ '/publications/' | relative_url }}) for publication details. The paper contains the full formulation, proofs, and numerical setup.

The results shown here are simulation studies. Next steps include joint path-and-speed optimization, receding-horizon control, and experimental validation using the SeaTrac SP-48.
