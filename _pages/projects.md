---
layout: single
title: "Projects"
permalink: /projects/
toc: true
toc_sticky: true
---

## Trajectory Optimization for Autonomous Spacecraft Docking
{: #robust-autonomous-docking}

### Overview
Autonomous spacecraft docking is a safety-critical problem that requires generating dynamically feasible trajectories while respecting strict constraints on relative position, velocity, attitude, and line-of-sight — all under uncertainty. This project focuses on designing a **robust, end-to-end trajectory optimization pipeline** suitable for real autonomous docking systems.

### What I Built
- Designed an **end-to-end, three-phase optimal control pipeline** for autonomous docking:
  - Far-range approach
  - Proximity operations
  - Terminal docking phase
- Implemented **hard safety and terminal constraints** inspired by NASA docking standards
- Formulated **uncertainty-aware terminal costs** using covariance-based perturbations
- Integrated **Monte Carlo sampling** to evaluate constraint satisfaction under uncertainty

### Technical Highlights
- Nonlinear optimal control formulated using **CasADi**
- Numerical optimization using **IPOPT**
- Explicit modeling of **relative position, velocity, and attitude constraints**
- Designed with future integration of **Kalman filter–based belief propagation** for closed-loop replanning

### Results & Impact
- Successfully generated **constraint-satisfying docking trajectories** for deterministic target states
- Demonstrated sensitivity of terminal feasibility to uncertainty in target pose
- Established a scalable foundation for **belief-space trajectory optimization** in future iterations

**Tools:** Python, CasADi, IPOPT, Optimal Control, State Estimation

📎 **Links**
- [Trajectory Animation](https://drive.google.com/file/d/13JnlbhTjiCzTOqh1IgnJ49QA6oTIqQhc/view?usp=sharing)
- ![3D Trajectory Visualization]({{ site.baseurl }}/assets/images/3d_Trajectory.png)

---

## Communication-Aware Multi-Robot Simulation Framework
{: #multi-robot-simulation}

### Overview
This project focuses on building a **physics-based, photo-realistic simulation environment** for studying coordination, communication constraints, and semantic mapping in multi-robot systems. The goal is to bridge the gap between algorithm development and deployment-ready robotic autonomy.

### What I Built
- Developed a **ROS2-based multi-robot simulation stack in C++**
- Integrated **Unity** for photo-realistic visualization and sensor simulation
- Led the **migration of a large codebase from ROS1 → ROS2**
- Implemented communication-aware coordination logic for multi-agent systems
- Integrated **SLAM pipelines and active perception components**

### Engineering Focus
- Modular ROS2 node architecture for scalability and maintainability
- Emphasis on **realistic sensing, communication latency, and resource constraints**
- Designed to support experimentation in **semantic mapping and multi-robot planning**

### Why It Matters
- Enables testing autonomy algorithms under **realistic communication and sensing constraints**
- Serves as a research and development platform for **multi-agent coordination**
- Directly applicable to **drone swarms, robotic fleets, and distributed autonomy**

**Tools:** C++, ROS2, Unity, SLAM, Multi-Robot Systems

📎 **Links**
- [GitHub Repository](https://github.com/Divyanshu-Singh-Chauhan/Resource-Aware-Coordination-AirSim)
- ![Multi-Robot Simulation Environment]({{ site.baseurl }}/assets/docs/drones_in_simenv.png)

---

## Lunar Anomaly Detection Using Deep Learning
{: #lunar-anomaly-detection}

### Overview
This project explores **unsupervised anomaly detection** on lunar surface imagery using deep learning. The objective was to automatically identify unusual surface features in large-scale orbital imagery without relying on labeled anomaly data.

### Approach
- Designed a **Variational Autoencoder (VAE)**-based anomaly detection pipeline
- Trained models on **terabytes of NASA Lunar Reconnaissance Orbiter (LRO) imagery**
- Deployed large-scale training workflows using **cloud-based infrastructure**
- Evaluated reconstruction error distributions to identify anomalous regions

### Results
- Successfully identified geologically unusual regions without supervised labels
- Demonstrated scalability of unsupervised learning for planetary science datasets
- Work accepted for presentation at **AbSciCon** and published in peer-reviewed venues

### Why It’s Relevant
- Experience building **end-to-end ML pipelines**, not just models
- Strong overlap with **perception systems** used in robotics and autonomy
- Demonstrates ability to handle **large datasets, noisy data, and weak supervision**

**Tools:** TensorFlow, Keras, VAEs, Computer Vision, Cloud Computing

📎 **Links**
- [Conference Paper](https://agu.confex.com/agu/abscicon21/meetingapp.cgi/Paper/1031511)
- ![Detected Lunar Anomalies]({{ site.baseurl }}/assets/docs/lunar_anomaly.png)
