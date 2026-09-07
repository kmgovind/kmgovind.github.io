---
layout: page
title: NSF Graduate Research Fellowship
description: My annual updates for the NSF GRFP
img: assets/img/nsf-grfp-logo-2362779762.png
importance: 1
category: research
related_publications: false
---

The **NSF Graduate Research Fellowship Program (GRFP)** is a prestigious fellowship awarded by the National Science Foundation to outstanding graduate students in science, technology, engineering, and mathematics (STEM) disciplines. The fellowship provides three years of financial support, including a stipend and tuition allowance, to help recipients pursue research-based master's and doctoral degrees at accredited U.S. institutions. The GRFP aims to recognize and support individuals who demonstrate potential for significant achievements in science and engineering research.

# Application

- [Personal Statement](/assets/pdf/grfp-personal.pdf)
- [Research Statement](/assets/pdf/grfp-research.pdf)

# 2025-2026 Award Year

## Intellectual Merit

Collecting spatiotemporally varying data is important for applications such as scientific monitoring, search and rescue, and energy farm siting. Sustainably powered robotic vehicles are uniquely suited to these missions because they can harvest energy directly from their environment, enabling persistent operation over long time horizons. However, operating such systems requires careful management of a fundamental tradeoff between energy and information: energy must be expended to move and sense the environment, while the value of information itself changes over time as the underlying phenomena evolve. In my research, I seek to characterize this tradeoff through a concept I term the “Information Value of Energy” (IVE) and to develop optimal planning and control strategies that account for both energy availability and information gain.

To begin addressing this problem, I studied the persistent energy allocation problem using a distance-maximizing optimal control formulation. In this work, I derived the energy-optimal strategy for maximizing distance traveled by a renewably powered vehicle. The results were published and presented at the 2025 IEEE Conference on Control Technology and Applications. Building on this result, I integrated the controller with an information-maximizing ergodic path planner to develop a hierarchical, energy-aware exploration algorithm. I validated this approach through field experiments using a solar-powered autonomous surface vessel deployed at Jordan Lake, North Carolina. The system was used to map wind speeds across the lake while prioritizing regions corresponding to a particular rated wind speed. The resulting dataset and experimental findings are currently under review as a journal publication in IEEE Transactions on Control Systems Technology.

Motivated by the limitations of the distance-maximizing formulation, and by the drawbacks of treating energy and information optimization separately, I next investigated an alternative optimization framework in which the objective was changed to information maximization under energy constraints along a fixed periodic path. Through this analysis, I derived an optimal controller that directly relates energy expenditure to expected information gain via the Information Value of Energy. This formulation provides a principled mechanism for modulating the robot’s speed: slowing down in regions expected to yield higher information and speeding up in less informative areas.

In ongoing work, I am extending this formulation by removing the fixed periodic path assumption and further generalizing the Information Value of Energy concept. The goal of this effort is to develop improved planning and control algorithms that jointly reason about energy availability and information gain. These methods will ultimately be validated through deployment on robotic systems operating in real-world environments.

## Broader Impacts

I continue to pursue my goal of expanding access to STEAM education opportunities for students in my communities. Through the InspireNC nonprofit, I have worked with high school students to teach the fundamentals of control algorithms and to help them implement these algorithms on robots that they designed and built. In addition, I recently began collaborating with the Triangle Robotics Association to help establish a community robotics hub in the Triangle region of North Carolina. This initiative aims to create a shared space where students can access tools, mentorship, and educational resources that may otherwise be unavailable to them, helping to reduce barriers to participation in robotics and engineering.

# 2024-2025 Award Year

## Intellectual Merit

My research focuses on the persistent optimal control of renewably-powered robotic vehicles. Since these robots source their energy from their environment, they are uniquely capable of conducting persistent missions to collect spatiotemporally varying data at high resolution. To accomplish such tasks, however, it is necessary to allocate energy intelligently. I addressed the persistent energy allocation problem by solving an optimal control problem, through which I prove the energy-optimal strategy to maximize distance traveled is to travel at a constant speed. This work is currently available as a preprint and is under review for presentation at the _IEEE Conference on Control Technology and Applications_.

I coupled this controller with an information-maximizing ergodic path planner to create a hierarchical energy-aware information-maximizing control algorithm. I tested this in the field using a solar-powered autonomous surface vessel at Jordan Lake, NC to map wind speeds across the lake, focusing on regions of a particular _rated wind speed_. The data and results from this field test are currently being prepared for publication in _IEEE Transactions on Control Systems Technology_.

In my ongoing work, I am working to characterize the relationship between information and energy, a term called Information-Value of Energy (IVE). With this term, we can design controllers that intelligently allocate and save energy based upon the information that can be collected using that energy, allowing for even more efficient exploration and data collection.

## Broader Impacts

I am continuing to work towards my goal of expanding access to STEAM education opportunities for students in my communities. I've worked with the InspireNC nonprofit to teach high school students basic control algorithms and helped them implement them in robots they designed and built. Further, I'm working with the nonprofit to establish a partnership with other nonprofit and corporate organizations in the area to set up a community workspace where students can have access to workshop tools, educational resources, and mentorship that may not otherwise be available to them.
