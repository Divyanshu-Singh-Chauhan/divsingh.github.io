---
layout: single
title: "Projects"
permalink: /projects/
excerpt: "Autonomy, estimation and control projects — from particle filter SLAM on real robots to spacecraft docking trajectory optimization."
toc: true
toc_sticky: true
toc_label: "Projects"
---

Work spanning perception and SLAM, state estimation, planning, and control — most of it validated on hardware or against Monte Carlo analysis rather than a single nominal run.

---

# Robotics &amp; Autonomy

## Particle Filter SLAM and Autonomous Navigation
{: #botlab-slam}

*Aug – Nov 2024 · C/C++, ROS, LiDAR, IMU · University of Michigan (ROB 550)*

### The problem
A differential drive robot has to navigate a multi-room indoor environment with no GPS and no prior map — it must localize and map simultaneously, then plan and execute collision-free paths, all on the robot's own compute.

### What I built
- **Particle filter SLAM** fusing 2D LiDAR scans with wheel odometry and IMU, maintaining an occupancy grid map built online.
- **A\* motion planning** over the live occupancy grid, with replanning as the map filled in.
- A **C/C++ implementation** running on the robot, with the estimation, mapping and planning components separated so each could be tested against logged data independently.

### What it demonstrated
- Reliable localization and navigation across a multi-room GPS-denied course on real hardware.
- The failure modes that only show up outside simulation: wheel slip corrupting odometry, particle depletion after aggressive turns, and map drift on loop closure.

**Stack:** C/C++, ROS, LiDAR, IMU, occupancy grid mapping, A\*
{: .dc-stack}

---

## Vision-Based Manipulation with a 5-DOF Arm
{: #armlab-manipulation}

*Aug – Nov 2024 · Python, ROS, OpenCV, RealSense · University of Michigan (ROB 550)*

![Overhead view of the ArmLab workspace: AprilTag calibration markers, detected and classified blocks with position estimates, and the 5-DOF arm]({{ "/assets/images/armlab-workspace.jpg" | relative_url }})
*Live detection output: AprilTags fixing the workspace frame, with each block segmented, classified by colour and labelled with its estimated world coordinates.*
{: .dc-caption}

### The problem
Detect, classify and manipulate objects in a structured workspace with a 5-DOF arm — accurately enough to pick, place and stack under competition time limits, using only an RGB-D camera for sensing.

### What I built
- **Automatic intrinsic and extrinsic camera calibration** using AprilTags, so the workspace frame could be re-established quickly between runs.
- **RGB-D object detection** with contour refinement and clustering to separate touching blocks and reject depth noise.
- **Forward and inverse kinematics** using the DH convention, with a geometry-based IK solution for grasp and placement poses.
- A **state machine** coordinating perception, planning and actuation through multi-stage autonomous tasks.

### Result
🥈 **Second place** in the ROB 550 final competition at the University of Michigan.

[📄 Project report (PDF)]({{ "/assets/docs/ROB_550_armlab.pdf" | relative_url }})

**Stack:** Python, ROS, OpenCV, Intel RealSense, AprilTags, kinematics, path planning
{: .dc-stack}

---

## Communication-Aware Multi-Robot Simulation
{: #multi-robot-simulation}

*Jan – May 2025 · C++, ROS2, Unity · Prof. Vasileios Tzoumas, University of Michigan*

![Multi-robot simulation environment]({{ "/assets/docs/drones_in_simenv.png" | relative_url }})

### The problem
Multi-robot coordination algorithms are usually developed against idealized assumptions — perfect communication, perfect sensing. Testing them honestly needs a simulator where bandwidth, latency and photo-realistic sensing are part of the experiment.

### What I built
- A **ROS2-based multi-robot simulation stack in C++**, with a modular node architecture so agents, sensors and coordination logic could be swapped independently.
- **Unity integration** for photo-realistic rendering and sensor simulation.
- The **ROS1 → ROS2 migration** of a large existing research codebase.
- Integration of **SLAM pipelines** (including SlideSLAM) for semantic mapping experiments.

### Why it matters
Gives a research group a platform where coordination and active perception algorithms can be evaluated under realistic communication and sensing constraints before they touch a real fleet.

[GitHub repository](https://github.com/Divyanshu-Singh-Chauhan/Resource-Aware-Coordination-AirSim)

**Stack:** C++, ROS2, Unity, SLAM, multi-robot systems
{: .dc-stack}

---

## Unattended Nanopore Library Prep and Sequencing
{: #lab-automation}

*2026 – present · Python, REST APIs, Arduino · Graduate research, University of Michigan*

![System architecture: a Python workstation controller drives the BioAssemblyBot over REST, an Arduino over serial, and the nanopore sequencer over the MinKNOW API]({{ "/assets/images/lab-automation-architecture.svg" | relative_url }})

### The problem
Preparing a nanopore sequencing library is a 21-step liquid handling protocol that someone has to stand at the bench and perform: opening the flow cell inlet port, priming it, loading buffer and sample in timed stages, sealing it, closing the lid, and then starting the run at the right moment. Every one of those steps is deterministic. None of them should need a person.

The goal is a single command that takes the cycle from an untouched flow cell to a running sequencer, unattended, and reports honestly if anything fails along the way.

### The system
Three subsystems have to cooperate, and none of them was designed to talk to the others:

- **BioAssemblyBot** — the robotic liquid handling platform that executes the prep protocol, driven over a **REST API on port 5050**: start a stored program, poll its state, report success or failure.
- **Nanopore sequencer (P2 Solo on GridION)** — driven over the **MinKNOW API** to start a run, stop a run, and query status.
- **Workstation controller** — the Python layer I'm building that sequences the whole cycle, owns the timing, and decides what happens when a stage doesn't return what it should.

### Where it stands

**Working**

- The sequencer is fully under remote control from the workstation — **start, stop and status all working** over the MinKNOW API, with no hands on the instrument.
- Connection method to the robot settled: REST over port 5050.
- Protocol decomposition settled (below), which is what makes the whole cycle expressible as a program.

**In progress**

- Verifying every BioAssemblyBot API endpoint — **in simulation mode first**, before any of it runs against wet samples.
- Encoding the 21 steps as stored programs on the robot.
- Arduino lid actuation and its handshake with the rest of the sequence.
- Data handoff and analysis once a run completes.
- One full unattended cycle, end to end.

### The interesting design problem
Step 19 is closing the lid — and the liquid handler physically cannot do it. That one mechanical gap forces the protocol to split into two robot programs with a foreign actuator in between:

| Stage | Steps | What happens |
|---|---|---|
| **BioApp A** | 1–18 | Open and prime the inlet port, clear trapped air, load 2 × 500 µL buffer with a 5-minute wait between, transfer 200 µL of sample, seal the port |
| **Arduino** | 19 | Close the lid — serial command from the controller, outside the robot's program |
| **BioApp B** | 20–21 | Wait 10 minutes, report ready to sequence |

So the controller isn't just a script that fires three API calls. It has to hold state across two robot programs, an actuator on a serial link, and an instrument API — and know, at each boundary, whether the previous stage actually finished or merely stopped responding.

### Engineering focus
Every endpoint is verified in simulation before it touches a real sample, and every stage boundary either confirms completion or raises — because an automation failure that gets silently swallowed at 2 a.m. costs a flow cell and a sample, not just a retry. This is the same failure-reporting discipline as the production automation I built at Standard Chartered, applied to hardware that can't be rolled back.

**Stack:** Python, REST APIs, MinKNOW API, Arduino, serial control, state machines, simulation-first testing
{: .dc-stack}

---

# Estimation &amp; Control

## Trajectory Optimization for Autonomous Spacecraft Docking
{: #robust-autonomous-docking}

*May 2025 – May 2026 · Python, CasADi, IPOPT · Graduate research, University of Michigan*

![Three-phase docking trajectory with approach cone and keep-out region]({{ "/assets/images/3d_trajectory.png" | relative_url }})

📎 [Trajectory animation](https://drive.google.com/file/d/13JnlbhTjiCzTOqh1IgnJ49QA6oTIqQhc/view?usp=sharing)

### The problem
Autonomous docking has to produce a dynamically feasible trajectory that respects hard constraints on relative position, velocity, attitude and line of sight — and it has to keep respecting them when the target's pose is uncertain.

### What I built
- The maneuver formulated as a **three-phase constrained optimal control problem** — far-range approach, proximity operations, terminal docking — solved with **CasADi** and **IPOPT**.
- **Hard safety and terminal constraints** inspired by NASA docking standards, including approach-cone and keep-out constraints.
- **Uncertainty-aware terminal costs** built from covariance-based quaternion perturbations, with **Monte Carlo sampling** to evaluate constraint satisfaction under uncertainty.
- A **modular Python pipeline** that decouples the optimization solver, the 6-DOF nonlinear dynamics, and EKF/UKF estimation — so planning, dynamics and estimation can be developed and tested independently.

### Results
- Constraint-satisfying docking trajectories generated across the full tested range of initial conditions, with **stable solver convergence** confirmed by Monte Carlo sampling.
- Quantified how sensitive terminal feasibility is to uncertainty in target pose.
- A structure that extends directly to **belief-space trajectory optimization** and closed-loop replanning.

**Stack:** Python, CasADi, IPOPT, optimal control, EKF/UKF, Monte Carlo analysis
{: .dc-stack}

---

## Spacecraft Attitude Determination and Control
{: #spacecraft-adcs}

*Aug – Dec 2025 · MATLAB, Raspberry Pi · University of Michigan (SPACE 584)*

### The problem
Take a spacecraft from tip-off — tumbling at roughly 1 rev/s — to stable pointing, using real sensor models and real hardware in the loop rather than an idealized simulation.

### What I built
- A **real-time Extended Kalman Filter** in MATLAB for a nonlinear attitude model, with **Monte Carlo consistency checks and 1σ error bounds** confirming the estimator was actually consistent, not just low-error on one run.
- **Magnetometer hard- and soft-iron calibration**, and **star tracker cluster identification** plus IR sun sensor center-of-pixel logic reaching 1° attitude determination accuracy.
- An **autonomous detumble controller** (B-dot) taking the vehicle from 1 rev/s to below 0.5 deg/s.
- **Hardware-in-the-loop testing** on a Raspberry Pi 5 with a Helmholtz coil, closing the simulation-to-hardware gap.

**Stack:** MATLAB, Raspberry Pi, EKF, Monte Carlo, HIL, magnetometer calibration
{: .dc-stack}

---

## Cascaded Control of a Flexible Inverted Pendulum
{: #flexible-pendulum}

*Jan – Apr 2026 · MATLAB, Simulink · University of Michigan*

### The problem
Stabilize a 6-state flexible inverted pendulum within a hard ±10° limit when the plant has a lightly damped structural resonance (ω<sub>n</sub> = 20 rad/s, ζ = 0.0002) sitting right where the controller wants bandwidth.

### What I built
- A **cascaded PID architecture** separating inner and outer loops by 6× in bandwidth, so position tracking and rapid angle stabilization don't fight each other.
- A **custom notch filter** to suppress the structural resonance without giving up loop bandwidth.
- Stability verified through **left-half-plane pole placement and the Nyquist criterion**, with robustness validated against 100 N impulse disturbances and near-zero structural damping.

### Why it's interesting
This is the case where a naive controller looks fine in simulation and shakes itself apart on hardware. The interesting engineering is in the frequency-domain reasoning, not the tuning.

**Stack:** MATLAB, Simulink, cascaded PID, notch filtering, Nyquist analysis
{: .dc-stack}

---

## Model Predictive Control for Cellular Reprogramming
{: #mpc-cellular}

*2026 – present · MATLAB, Python · University of Michigan*

Casting cellular reprogramming as a **constrained receding-horizon optimal control problem**: designing the cost and constraint formulation over a nonlinear model, and evaluating closed-loop convergence in MATLAB and Python simulation. A control problem where the plant is biological, the state is only partially observable, and the constraints are what keep the trajectory physically meaningful.

**Stack:** MATLAB, Python, MPC, nonlinear optimization
{: .dc-stack}

---

# Machine Learning &amp; Perception

## Neural Anomaly Detection on Lunar Imagery
{: #lunar-anomaly-detection}

*Python, TensorFlow, VAEs · Published at AbSciCon 2022*

![Detected lunar anomalies]({{ "/assets/docs/lunar_anomaly.png" | relative_url }})

### The problem
Find unusual surface features across terabytes of NASA Lunar Reconnaissance Orbiter imagery — with no labeled anomalies to train on.

### Approach
- A **variational autoencoder** anomaly detection pipeline, using reconstruction error distributions to flag anomalous regions.
- Trained on **terabytes of LRO imagery** using cloud-based training infrastructure.

### Results
- Identified geologically unusual regions without supervised labels.
- Accepted for presentation at **AbSciCon 2022**.

[Conference paper](https://agu.confex.com/agu/abscicon21/meetingapp.cgi/Paper/1031511)

**Stack:** TensorFlow, Keras, VAEs, computer vision, cloud computing
{: .dc-stack}

---

## Reinforcement Learning for Grasp Control
{: #ddpg-grasping}

*2020 – 2021 · Python, ROS, Gazebo · B.Tech thesis, IIT Guwahati*

A **DDPG agent** for continuous closed-loop grasp control of a robotic hand, trained and evaluated end to end in a ROS/Gazebo simulation. The thesis work that pulled me from mechanical engineering toward autonomy.

**Stack:** Python, ROS, Gazebo, DDPG, reinforcement learning
{: .dc-stack}

---

## Image Tampering Localization
{: #image-tampering}

*May – Aug 2020 · Python, deep learning · HyperVerge*

Convolutional and GAN-based autoencoders to localize tampered regions in document images, including a **custom Conv2D layer** that raised manipulation detection precision from 75% to 90%, at 91% overall accuracy.

**Stack:** Python, TensorFlow, GANs, autoencoders
{: .dc-stack}
