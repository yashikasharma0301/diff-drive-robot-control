# Differential Drive Robot Control in ROS 2

This project demonstrates the creation of a differential drive robot simulation in ROS 2. It includes a `myrobot_description` package to load and visualize the robot in RViz, and a separate `myrobot_gazebo` package with an empty world to spawn the robot in Gazebo. The project integrates velocity command plugins (`/cmd_vel`) and enables robot control using the `teleop_twist_keyboard` package to verify movement in the simulated environment. 

Click [here](https://youtu.be/SgQI-Ug09Po) for the simulation video.

## System Requirements

- **Ubuntu**: 22.04 LTS
- **ROS 2**: Humble Hawksbill
- **Gazebo**: Ignition Garden

## Usage

### Prerequisites

Install required ROS 2 packages:

```bash
sudo apt install ros-humble-robot-state-publisher \
                 ros-humble-joint-state-publisher \
                 ros-humble-xacro \
                 ros-humble-teleop-twist-keyboard \
                 ros-humble-ros-gz-sim \
                 ros-humble-ros-gz-bridge
```

### Installation & Setup

1. **Create Workspace and Clone Repository**
```bash
mkdir -p my_ws/src && cd my_ws/src
git clone https://github.com/yashikasharma0301/diff_drive_robot_control.git .
```

2. **Build the Workspace**
```bash
cd ..
colcon build
```

3. **Source the Workspace**
```bash
source install/setup.bash
```

### Running the Simulation

1. **Launch Robot Visualization in RViz**
```bash
ros2 launch myrobot_description myrobot.launch.py
```
<img width="1852" height="1018" alt="Screenshot from 2025-07-23 16-03-32" src="https://github.com/user-attachments/assets/2e294285-5502-4e84-a8f0-2ba8f47d774a" />

If the robot model doesn't load automatically in RViz, click on the RobotModel dropdown arrow in the RViz panel and type **/robot_description** infront of **Description Topic**

2. **Launch Gazebo Simulation**

Source the workspace again if opening a new terminal and run:
```bash
ros2 launch myrobot_gazebo myrobot.launch.py
```

3. **Control the Robot**

In a new terminal, start keyboard teleoperation:
```bash
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
<img width="1852" height="1018" alt="Screenshot from 2025-07-23 16-04-55" src="https://github.com/user-attachments/assets/5a54b62b-8592-44a7-85db-9308451c1713" />

**Control Keys:**
- `i` - Move forward
- `k` - Stop
- `j` - Turn left  
- `l` - Turn right
- `u` - Move forward + turn left
- `o` - Move forward + turn right
- `m` - Move backward + turn left
- `.` - Move backward + turn right
- `,` - Move backward

## Credits & References

**Robot Model**: This project uses a URDF model adapted from the TortoiseBot example in the [OSRF ROS Book](https://github.com/osrf/rosbook/blob/master/code/tortoisebot/tortoisebot.urdf). The original model has been modified for ROS 2 Humble and Gazebo Ignition integration.

**Original Authors**: Open Source Robotics Foundation (OSRF)
