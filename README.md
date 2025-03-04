# wamv_gz
Simple WAM-V Simulation for ROS 2 Jazzy + Gazebo Harmonic on Ubuntu 24.04 based on [VRX](https://github.com/osrf/vrx)

[Screencast from 2024-12-29 18-36-39.webm](https://github.com/user-attachments/assets/71d9622f-a003-4d59-bfaf-0f32e410608c)

## Installation
1. Download [ROS 2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html)
2. Download [Gazebo Harmonic](https://gazebosim.org/docs/harmonic/install_ubuntu/)
3. Download ros_gz with `sudo apt-get install ros-jazzy-ros-gz`
4. Create a ROS 2 workspace and clone this repository into the /src directory
5. Run the following terminal commands in the root directory of the ROS 2 workspace:
```bash
colcon build
source install/setup.bash
ros2 launch wamv_gz wamv_launch.py
```
4. In a separate terminals you can run the following commands to move the WAM-V:
```bash
# Thruster activation. Recommended range is -10.0 to 10.0
ros2 topic pub /wamv/thrusters/left/thrust std_msgs/msg/Float64 "data: 10.0"
ros2 topic pub /wamv/thrusters/right/thrust std_msgs/msg/Float64 "data: -4.0"
```

5. Other topics are as follows and can be seen using `ros2 topic echo <topic_name>`:
```bash
/wamv/ground_truth/odometry
/wamv/sensors/camera/front/camera_info
/wamv/sensors/camera/front/image
/wamv/sensors/front_lidar/points
/wamv/sensors/front_lidar/scan
/wamv/sensors/gps/gps/fix
/wamv/sensors/imu/imu/data
```
