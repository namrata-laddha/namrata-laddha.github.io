---
layout: page
title: payload optimization autonomous drone
description: A custom flight control PCB with integrated high-current motor drive and sensor array, built for emergency package delivery.
importance: 2
category: work
related_publications: true
---

A delivery drone designed around a single question: how much more payload can you carry if the electronics stop being an afterthought? First-author work, published as {% cite laddha2023drone %}.

## The problem

Emergency delivery — medicine, documents, small critical supplies — is exactly the case where road traffic hurts most and where a drone should win. Two things get in the way: limited battery endurance, and increasingly congested low-altitude airspace.

## What I built

I designed and fabricated the custom flight control PCB. Rather than stacking a commercial flight controller on top of separate ESCs and a sensor breakout, the board integrates:

- **High-current motor drive circuits**, placed and routed on the same board as the controller to cut interconnect mass and wiring losses
- **An onboard sensor array** feeding the control loop directly
- **Real-time embedded execution** of constraint-based flight control, so payload and routing constraints are enforced in flight rather than pre-planned on the ground

Consolidating these onto one board reduces the mass that does not contribute to payload — which is the whole point, since every gram of avionics is a gram of medicine you cannot carry.

## Approach

The study pairs that hardware work with two analyses: payload optimization, which examines where mass can be removed from the airframe and components without compromising performance, and traffic avoidance, which plans routes around congested airspace and obstacles using real-time monitoring. Together they extend flight time and reduce energy per delivery.
