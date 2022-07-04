---
title: ADS
date: 2022-1-21 15:23:02
tags:
 - AI

---

Created: 2022-1-6 20:05:09

Modified: 2022-1-21 15:23:02

<!--more-->

# computer vision

## video

attack/safety

sim、test

# Model

lane-change: 

traditional rule-based model: assesses the positions and speeds + decides gap acceptance

Reinforcement Learning-based: end-to-end; decision-making part (deep Q-learning) +  an optimal lattice planner + a model predictive controller

## Apollo

map:

# industry

## safety

read: https://developer.nvidia.com/blog/training-self-driving-vehicles-challenge-scale/, https://www.rand.org/content/dam/rand/pubs/research_reports/RR1400/RR1478/RAND_RR1478.pdf

# LGSVL with  Apollo

https://www.youtube.com/watch?v=Ucr0aM334_k: about API

*LGSVL* graphical simulator (LG. Lgsvl simulator. [Online]. Available: https://www.lgsvlsimulator.com/) that supports both freeway and urban road structures.

api collect data: slow , so use bridge (like apollo)?# Typora

# CARLA

carla (CARLA: An Open Urban Driving Simulator)

data (routes and scenarios as source -> rbg, lidar) 

​    route (a sequence of waypoints (and optionally a weather condition))

​    scenario (a trigger transform (location and orientation) and other actors present in that scenario (optional))

```
run on colab:
https://github.com/carla-simulator/carla/issues/2820
```

![image-20220228161225241](ADS/image-20220228161225241.png)
