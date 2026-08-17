---
layout: page
title: thrust-vectored model rocket
description: Dual-servo TVC, servo-actuated parachute recovery, and a custom flight computer — 384 N peak thrust, 320 N-s total impulse.
importance: 1
category: work
related_publications: true
---

A model rocket built to carry the control systems normally reserved for much larger vehicles: active thrust vector control, a reliable recovery system, and onboard flight data acquisition. Developed at KJ Somaiya College of Engineering between July and December 2024, and published as {% cite thorat2024rocket %}.

## What it does

The vehicle steers itself during powered flight and recovers itself afterwards. A dual-servo gimbal deflects the motor under closed-loop control, and a servo-actuated hexagonal parachute deploys for descent, leaving the airframe reusable.

## Design

**Thrust vector control.** A dual-servo mechanism gimbals the motor mount, driven by attitude feedback from an MPU6050 gyroscope. The control loop corrects deviations during the burn rather than relying on fin authority alone.

**Recovery.** A hexagonal parachute with servo-actuated deployment brings the vehicle down intact. Deployment is commanded by the flight computer rather than a purely pyrotechnic or timer-based trigger.

**Propulsion and structure.** KNSB (potassium nitrate sorbitol) solid propellant in a reusable combustion chamber, with an interchangeable fin can so aerodynamic configurations can be swapped between flights without rebuilding the airframe.

**Avionics.** A custom Arduino-based flight computer handles sensor acquisition, control law execution, and recovery sequencing.

## Results

| Metric | Value |
| :----- | :---- |
| Maximum thrust | 384 N |
| Total impulse | 320 N-s |

Flight testing validated both the thrust vectoring system's contribution to flight stability and the reliability of the recovery sequence.
