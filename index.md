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
    <img src="{{ '/assets/images/lab-automation-architecture.svg' | relative_url }}" alt="System architecture for unattended nanopore library prep and sequencing">
    <div>
      <h3><a href="{{ '/projects/#lab-automation' | relative_url }}">Unattended Nanopore Library Prep and Sequencing</a></h3>
      <p>Current research: one command takes a 21-step liquid handling protocol from an untouched flow cell to a running sequencer. A Python controller drives a BioAssemblyBot over REST, an Arduino over serial, and the sequencer over the MinKNOW API — holding state across all three and failing loudly rather than silently.</p>
      <p class="dc-tags">Python · REST APIs · MinKNOW · Arduino · State machines</p>
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
    <img src="{{ '/assets/images/armlab-workspace.jpg' | relative_url }}" alt="ArmLab workspace with AprilTag calibration and detected blocks labelled with world coordinates">
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
| **Graduate Research Assistant** — Robotic Lab Automation | University of Michigan | 2026 – present |
| **Graduate Research Assistant** — Trajectory Optimization | University of Michigan | May 2025 – May 2026 |
| **Python Developer** — Cybersecurity Automation | Standard Chartered Bank | 2021 – 2024 |
| **Deep Learning Intern** | HyperVerge | May – Aug 2020 |

As a **Research Assistant** I'm currently automating a nanopore sequencing workflow end to end: a Python controller that drives a BioAssemblyBot liquid handling robot over its REST API, an Arduino for the one mechanical step the robot can't perform, and the sequencer itself over the MinKNOW API. Remote start, stop and status on the sequencer are working; the 21-step prep protocol is decomposed and being encoded on the robot. [Read the full write-up →]({{ "/projects/#lab-automation" | relative_url }})

Three years of production software engineering sit underneath the research: FastAPI microservices and SOAR automation under CI/CD with Bitbucket code review and pytest, cutting incident response time by 40%, plus an end-to-end supervised phishing detection pipeline reaching 83% accuracy on production data.

---

## Currently

- **Unattended nanopore library prep and sequencing** — a Python controller sequencing a BioAssemblyBot (REST), an Arduino lid actuator (serial) and a P2 Solo sequencer (MinKNOW API) through a 21-step protocol, with every endpoint verified in simulation before it touches a sample. [Details →]({{ "/projects/#lab-automation" | relative_url }})
- **Model predictive control for cellular reprogramming** — casting a biological reprogramming problem as constrained receding-horizon optimal control, in MATLAB and Python. [Details →]({{ "/projects/#mpc-cellular" | relative_url }})

---

## Credentials

- **M.S.E. Aerospace Engineering**, University of Michigan — Autonomous Systems &amp; Control, GPA 3.77/4.00 (2026)
- **B.Tech. Mechanical Engineering**, IIT Guwahati (2021)
- Publications in *PLOS One* and *AbSciCon 2022* — [see publications]({{ "/publications/" | relative_url }})
