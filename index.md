---
layout: splash
title: "Divyanshu Singh Chauhan"
permalink: /
excerpt: "Robotics &amp; autonomy engineer — perception, SLAM, state estimation, planning and control. C++, Python and ROS2, taken from simulation onto real hardware."
header:
  overlay_color: "#0a1018"
  overlay_image: /assets/images/hero-banner.png
  overlay_filter: 0.25
  actions:
    - label: "View projects"
      url: /projects/
    - label: "Download résumé"
      url: /assets/docs/Resume_Divyanshu_Robotics.pdf
---

I build the parts of an autonomy stack that have to survive contact with reality: estimating where a robot is when GPS is gone, planning a motion that respects hard safety limits, and closing the loop on real hardware. My graduate work at the University of Michigan is in trajectory optimization and state estimation for spacecraft; my hands-on work is particle filter SLAM, LiDAR–IMU fusion and manipulation on real robots.

Before graduate school I spent three years shipping production Python — microservices, CI/CD, code review, automated testing — which is why I care as much about whether a pipeline is testable and debuggable as whether the algorithm is elegant.

<div class="dc-cta" markdown="1">
**Open to full-time robotics / autonomy roles from May 2026.** [Get in touch →]({{ "/contact/" | relative_url }})
</div>

---

## What I work on

<div class="dc-grid">
  <div class="dc-card">
    <h3>Perception &amp; SLAM</h3>
    <p>Particle filter SLAM, occupancy mapping, LiDAR + IMU sensor fusion, RGB-D perception with RealSense. Validated in GPS-denied indoor environments on real differential drive hardware.</p>
    <p class="dc-tags">C++ · Python · ROS2 · LiDAR · RealSense</p>
  </div>
  <div class="dc-card">
    <h3>State Estimation</h3>
    <p>EKF, UKF and particle filters for safety-critical autonomy, with Monte Carlo consistency checks and 1σ error-bound analysis rather than a single lucky run.</p>
    <p class="dc-tags">EKF · UKF · Monte Carlo · Sensor calibration</p>
  </div>
  <div class="dc-card">
    <h3>Planning &amp; Trajectory Optimization</h3>
    <p>A* motion planning on real robots, and constrained nonlinear optimal control in CasADi/IPOPT for multi-phase maneuvers under hard terminal constraints.</p>
    <p class="dc-tags">A* · CasADi · IPOPT · MPC</p>
  </div>
  <div class="dc-card">
    <h3>Control &amp; Hardware in the Loop</h3>
    <p>PID, cascaded and model predictive control, taken from simulation to hardware — Raspberry Pi testbeds, Helmholtz coils, Arduino instrument control.</p>
    <p class="dc-tags">PID · MPC · HIL · Simulink</p>
  </div>
</div>

---

## Selected projects

<div class="dc-projects">

  <div class="dc-project">
    <img src="{{ '/assets/images/3d_trajectory.png' | relative_url }}" alt="Three-phase docking trajectory with approach cone and keep-out sphere">
    <div>
      <h3><a href="{{ '/projects/#robust-autonomous-docking' | relative_url }}">Autonomous Spacecraft Docking Under Uncertainty</a></h3>
      <p>A three-phase docking maneuver posed as a constrained trajectory optimization problem in CasADi/IPOPT, with uncertainty-aware terminal constraints and Monte Carlo validation of solver convergence across the full tested range of initial conditions.</p>
      <p class="dc-tags">Python · CasADi · IPOPT · EKF/UKF · Monte Carlo</p>
    </div>
  </div>

  <div class="dc-project">
    <div class="dc-project__noimg"></div>
    <div>
      <h3><a href="{{ '/projects/#botlab-slam' | relative_url }}">Particle Filter SLAM &amp; Autonomous Navigation (BotLab)</a></h3>
      <p>A* planning and particle filter SLAM with LiDAR–IMU fusion, written in C/C++ for a real differential drive robot navigating a multi-room GPS-denied environment.</p>
      <p class="dc-tags">C/C++ · ROS · LiDAR · IMU · Occupancy mapping</p>
    </div>
  </div>

  <div class="dc-project">
    <img src="{{ '/assets/docs/drones_in_simenv.png' | relative_url }}" alt="Multi-robot simulation environment rendered in Unity">
    <div>
      <h3><a href="{{ '/projects/#multi-robot-simulation' | relative_url }}">Communication-Aware Multi-Robot Simulation</a></h3>
      <p>A physics-based, photo-realistic ROS2 + Unity simulator for studying coordination and semantic mapping under communication constraints, including a ROS1 → ROS2 migration of the codebase.</p>
      <p class="dc-tags">C++ · ROS2 · Unity · SLAM</p>
    </div>
  </div>

  <div class="dc-project">
    <div class="dc-project__noimg"></div>
    <div>
      <h3><a href="{{ '/projects/#armlab-manipulation' | relative_url }}">Vision-Based Robotic Manipulation (ArmLab)</a></h3>
      <p>Perception, kinematics and planning for a 5-DOF arm: AprilTag camera calibration, RGB-D object detection, DH forward/inverse kinematics and a state machine driving multi-stage pick, place and stack tasks. Second place in the ROB 550 final competition.</p>
      <p class="dc-tags">Python · ROS · OpenCV · RealSense · Kinematics</p>
    </div>
  </div>

</div>

[See all projects, including spacecraft ADCS, flexible-structure control and lab automation →]({{ "/projects/" | relative_url }})

---

## Experience

| | | |
|---|---|---|
| **Graduate Research Assistant** — Trajectory Optimization | University of Michigan | May 2025 – May 2026 |
| **Python Developer** — Cybersecurity Automation | Standard Chartered Bank | 2021 – 2024 |
| **Deep Learning Intern** | HyperVerge | May – Aug 2020 |

Three years of production software engineering sit underneath the research: FastAPI microservices and SOAR automation under CI/CD with Bitbucket code review and pytest, cutting incident response time by 40%, plus an end-to-end supervised phishing detection pipeline reaching 83% accuracy on production data.

---

## Currently

- **Lab automation at the University of Michigan** — integrating a robotic liquid-handling platform with a benchtop sequencing instrument over REST, plus Arduino-driven actuation, so a multi-step sample preparation protocol runs unattended end to end.
- **Model predictive control for cellular reprogramming** — casting a biological reprogramming problem as constrained receding-horizon optimal control, in MATLAB and Python.

---

## Credentials

- **M.S.E. Aerospace Engineering**, University of Michigan — Autonomous Systems &amp; Control, GPA 3.77/4.00 (2026)
- **B.Tech. Mechanical Engineering**, IIT Guwahati (2021)
- Publications in *PLOS One* and *AbSciCon 2022* — [see publications]({{ "/publications/" | relative_url }})
