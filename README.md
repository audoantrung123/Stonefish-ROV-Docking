# Stonefish-ROV-Docking

![Status](https://img.shields.io/badge/status-in_progress-yellow)
![Platform](https://img.shields.io/badge/platform-ROS-blue)
![Simulator](https://img.shields.io/badge/simulator-Stonefish_1.5-orange)

This repository contains the simulation environment and control code for developing an autonomous docking system for a Remotely Operated Vehicle (ROV) in the **Stonefish simulator**. The primary goal is to create a robust testbed for validating advanced sensor fusion and control algorithms under significant environmental disturbances, such as ocean currents and poor visibility.

This project serves as the technical implementation for a Ph.D. research proposal at the University of Houston, under the advisory of Dr. Aaron Becker.

Video Simulation: https://youtu.be/noezsi-n5so

## Intended System Architecture

The complete system is designed to achieve robust autonomous docking by integrating several key modules:

* **Localization:** A sensor fusion pipeline using an **Extended Kalman Filter (EKF)** to fuse data from an IMU, DVL, and vision (AprilTag/Aruco) for accurate 6-DoF pose estimation.
* **Planning:** A real-time path planner to generate smooth, dynamically feasible trajectories to the docking station.
* **Control:** A layered control architecture featuring **PID** for basic stabilization and a **Model Predictive Controller (MPC)** augmented with **Control Barrier Functions (CBF)** for safe and precise near-field docking.
* **Vision:** A computer vision module for detecting the docking station (using Aruco/AprilTags) and estimating its relative pose.

---

## 🚧 Current Project Status

**Note: This project is currently in the initial development phase.**

As of the current commit, the following components have been successfully implemented and validated:

* **Stonefish Environment:** Successfully launched the ROV and docking station models in a custom Stonefish 1.5 scenario.
* **Camera & Vision Pipeline:** Established a ROS topic streaming real-time camera data from the ROV. This feed is successfully processed by an `aruco_detect` node, which can identify and publish the pose of Aruco markers.
* **Basic Control:** A foundational **PID controller** is implemented for basic motion control, allowing the ROV to hold its position (station-keeping) and respond to simple commands.

### Simulation Screenshots

<p align="center">
  <img src="https://github.com/user-attachments/assets/b06a3a0f-4efa-4f7c-aaaf-41903f593e73" width=" 50%"/>
</p>
<p align="center"> Figure 1. Aruco Tag Detection from the ROV's camera feed  </p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/f900060f-42d7-4968-bb99-68561efd60ec" width=" 50%"/>
</p>
<p align="center"> Figure 2. Surface view of the docking station (with Aruco marker) in Stonefish( GIRONA500)  </p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/814bd27d-0762-43ff-a167-388bb3318d7a" width=" 50%"/>
</p>
<p align="center"> Figure 3. BlueROV2 model in the Stonefish Simulator  </p>

---

## 🚀 Future Work (Roadmap)

The immediate next steps involve integrating the current components and building out the full architecture:

1.  **EKF Implementation:** Develop the Extended Kalman Filter node to fuse the current `aruco/pose` output with IMU and DVL data.
2.  **MPC/CBF Controller:** Implement the Model Predictive Controller and Control Barrier Function for the final, high-precision docking maneuver.
3.  **Stress Testing:** Inject current disturbances into the Stonefish environment to validate the robustness of the controllers.
4.  **Monte-Carlo Evaluation:** Conduct extensive trials to quantify system performance (docking success rate, position error, etc.).



