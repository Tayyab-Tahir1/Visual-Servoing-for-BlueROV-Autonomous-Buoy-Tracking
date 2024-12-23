# Visual Servoing for BlueROV: Autonomous Buoy Tracking

## Overview

This repository contains the implementation of **visual servoing** on a BlueROV to autonomously track an orange buoy in an underwater environment. The project leverages computer vision techniques, a Proportional (P) controller, and the Robot Operating System (ROS) for precise navigation and control. 

The system integrates image processing, real-time control, and robotics concepts to demonstrate advanced autonomy for underwater robotics. This work highlights the fusion of vision-based sensing and control systems in dynamic and visually complex environments like underwater scenarios.

---

## Features

- **Visual Servoing (IBVS)**: Implements Image-Based Visual Servoing for robust object tracking.
- **Proportional Controller**: Adjusts BlueROV velocity based on error between the current and desired positions.
- **Real-time ROS Integration**: Uses ROS to handle communication between sensors, actuators, and control algorithms.
- **Feature Detection and Tracking**:
  - HSV color space conversion.
  - Contour detection and centroid calculation for buoy tracking.
- **Degrees of Freedom Control**:
  - Yaw-Heave and Sway-Heave control.
  - 5-degrees of freedom control (excluding pitch).
- **Interaction Matrix Computation**:
  - Estimates motion dynamics between current and desired states using Jacobian matrices.

---

## Methodology

### 1. System Setup
- **ROS Environment**: Configured ROS with the `autonomous_rov` package for data processing and control.
- **Camera Calibration**: Tuned HSV thresholds for reliable buoy detection under varying underwater conditions.

### 2. Image Processing
- Converted RGB frames to HSV color space for color segmentation.
- Detected contours and calculated the centroid of the buoy for real-time tracking.

### 3. Control System
- Implemented a Proportional (P) controller to compute control signals for yaw, heave, sway, and other degrees of freedom.
- Transformed camera-frame velocities to body-frame velocities for accurate motion execution.

### 4. ROS Integration
- Published camera velocity, robot velocity, and error as ROS topics for seamless communication.

### 5. Control Modes
- **Yaw-Heave Control**: Maintained alignment with the buoy while adjusting depth.
- **Sway-Heave Control**: Enabled lateral movement for precise tracking.
- **5-Degrees of Freedom Control**: Controlled all degrees of freedom except pitch to stabilize the ROV.

---

## Results

### Key Observations
- The P controller successfully reduced tracking errors for all tested degrees of freedom.
- The system demonstrated robust responsiveness in:
  - Simulated bag files.
  - Preliminary in-air tests.
  - Real-world underwater tank tests.
- Oscillations during tracking were observed due to limitations of the P controller in handling all five degrees of freedom.

### Performance Highlights
- Error convergence to ≤ 0.1m in 5-degree control mode.
- Real-time responsiveness validated through trajectory plots and ROS velocity topics.

---

## Prerequisites

- **Robot Operating System (ROS)**
- **Python (3.8 or later)** with OpenCV
- **BlueROV** hardware
- Camera module calibrated for underwater conditions

---

