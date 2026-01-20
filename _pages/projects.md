---
layout: single
title: "Projects"
permalink: /projects/
toc: true
toc_sticky: true
---

## Trajectory Optimization for Spacecraft Docking
{: #robust-autonomous-docking}

### Problem
Autonomous spacecraft docking requires precise trajectory planning under uncertainty while satisfying strict safety and terminal constraints.

### My Contribution
- Designed a **3-phase optimal control deterministic pipeline** for docking
- Incorporating **uncertainty-aware terminal constraints**
- Using **Monte Carlo sampling and covariance-based perturbations**

### Tools & Methods
Python, CasADi, IPOPT, Optimal Control, State Estimation

### Results
- Constraint-satisfying docking trajectories for deterministic target's location
- Working towards robustness against uncertainty in target's location

📎 **Links:**  
- [GitHub Repository](https://github.com/your-link)
- ![Trajectory plot]((assets/docs/3D_Trajectory.pdf))

---

## Communication-Aware Multi-Robot Simulation
{: #multi-robot-simulation}

### Overview
A physics-based and photo-realistic simulator for multi-robot systems performing semantic mapping.

### Key Work
- ROS2 middleware in **C++**
- Unity-based visualization
- Migration from ROS1 → ROS2
- Integration of SLAM and active perception

📎 **Links:**  
- [GitHub Repo](https://github.com/Divyanshu-Singh-Chauhan/Resource-Aware-Coordination-AirSim)
- ![Simulation Environment with Drones](assets/docs/drones_in_simenv.png)

---

## Lunar Anomaly Detection Using Deep Learning
{: #lunar-anomaly-detection}

### Goal
Detect anomalies on lunar surface imagery using unsupervised learning.

### Approach
- Variational Autoencoders trained on NASA LRO data
- Large-scale cloud-based training pipeline

📎 **Links:**  
- [Paper](https://agu.confex.com/agu/abscicon21/meetingapp.cgi/Paper/1031511)
- ![Anomalies on the Lunar Anomalies](assets/docs/lunar_anomaly.png)
