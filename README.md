# DG3F-B ROS 2

[![CI](https://github.com/tesollodelto/dg3f_b_ros2/actions/workflows/ci.yml/badge.svg)](https://github.com/tesollodelto/dg3f_b_ros2/actions/workflows/ci.yml)
![ROS 2 Humble](https://img.shields.io/badge/ROS_2-Humble-blue?logo=ros)
![ROS 2 Jazzy](https://img.shields.io/badge/ROS_2-Jazzy-blue?logo=ros)

> **Note:** This model has been discontinued. This repository is kept for reference.

ROS 2 packages for the **Delto Gripper DG3F-B** (3-finger, basic type).

## Packages

| Package | Description |
|---|---|
| `dg3f_b_description` | URDF/xacro model, meshes, and RViz display launch |
| `dg3f_b_driver` | ros2_control hardware driver and controller launch files |
| `dg3f_b_moveit_config` | MoveIt 2 configuration (SRDF, planners, mock hardware) |

## Dependencies

This repository requires the following packages to build:

```bash
# Clone into your ROS 2 workspace src directory
git clone https://github.com/tesollodelto/dg_hardware.git
git clone https://github.com/tesollodelto/dg_tcp_comm.git
```

- [`delto_hardware`](https://github.com/tesollodelto/dg_hardware) — Unified hardware interface for Delto grippers
- [`delto_tcp_comm`](https://github.com/tesollodelto/dg_tcp_comm) — TCP communication library for Delto grippers

## Build

```bash
cd ~/ros2_ws
colcon build --packages-select dg3f_b_description dg3f_b_driver dg3f_b_moveit_config
source install/setup.bash
```

## Launch

```bash
# Hardware driver
ros2 launch dg3f_b_driver dg3f_b_driver.launch.py

# Mock hardware (no device required)
ros2 launch dg3f_b_driver dg3f_b_mock.launch.py

# MoveIt (mock hardware, default)
ros2 launch dg3f_b_moveit_config dg3f_b_moveit.launch.py

# MoveIt (real hardware)
ros2 launch dg3f_b_moveit_config dg3f_b_moveit.launch.py use_mock:=false delto_ip:=169.254.186.72
```