# ERICC 2 - ENSIT Vision Edition (5-DOF Robotic Arm Digital Twin)

Full CAD-to-Simulation Digital Twin of the 5-DOF **ERICC 2** educational robotic manipulator equipped with a 5th-axis RGB vision module, designed from scratch in **SOLIDWORKS** and simulated in **ROS 2 Jazzy** and **Gazebo Harmonic**.

## Key Features
- **Complete 3D CAD & URDF/Xacro:** All 6 links (`base_link` through `camera_roll_link`) modeled in SOLIDWORKS with exact mass, center of gravity, and 6-component inertia tensors (`Ixx`, `Iyy`, `Izz`, `Ixy`, `Ixz`, `Iyz`).
- **Physics & Studio Rendering:** Simulated in Gazebo Harmonic (`ogre2`) with Physically Based Rendering (PBR) metallic materials, studio lighting, and joint damping/friction.
- **Closed-Loop Control (`ros2_control`):** 5-DOF `JointTrajectoryController` (`/arm_controller/joint_trajectory`) and real-time `/joint_states` feedback.
- **Onboard Vision Sensor:** Simulated 640x480 RGB camera mounted on `camera_roll_link` bridged to `/camera/image_raw` via `ros_gz_bridge`.

## Quick Launch
```bash
cd ~/ros2_ws && colcon build --packages-select ericc2_description
source ~/ros2_ws/install/setup.bash
ros2 launch ericc2_description gazebo.launch.py
```
