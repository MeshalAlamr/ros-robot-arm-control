# ros-robot-arm-control
This project is prepared for the submission of the first task in the AI & Robotics path of the remote summer training offered by Smart Methods.

## Output 
The goal of this project is to control a robot arm using MoveIt in RViz and to visualize the simulation in Gazebo.

The GIF below shows the result obtained after completing the project.

![output](https://raw.githubusercontent.com/MeshalAlamr/ros-robot-arm-control/main/output.gif)

# Tutorial
## Prerequisites
- [Ubuntu 18.04.5 LTS](https://releases.ubuntu.com/18.04.5/)
- [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu)

## Procedure
1) Create a [catkin workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace).
2) Clone the arduino_robot_arm package by Smart Methods to the catkin_ws source file as so: 
```
$ cd ~/catkin_ws/src 
$ sudo apt install git
$ git clone https://github.com/smart-methods/arduino_robot_arm
```
3) Install dependencies and compile the package.
```
$ cd ~/catkin_ws 
$ rosdep install --from-paths src --ignore-src -r -y
$ sudo apt-get install ros-melodic-moveit
$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
$ catkin_make
```
Now, you may run the following to start an Rviz simulation of the robot arm that can be controlled by the joint_state_publisher through GUI sliders:
```
$ roslaunch robot_arm_pkg check_motors.launch
```
4) To visualize the simulation in Gazebo start off by changing the permission as so:
```
$ cd catkin/src/arduino_robot_arm/robot_arm_pkg/scripts
$ sudo chmod +x joint_states_to_gzebo.py
```
5) Now launch the simulation as so:
```
$ roslaunch robot_arm_pkg check_motors.launch
$ roslaunch robot_arm_pkg check_motors_gazebo.launch
$ rosrun robot_arm_pkg joint_states_to_gazebo.py
```
6) To control the robot arm through MoveIt in Rviz as per the output section above, start off by installing MoveIt through the setup assistant.
```
$ roslaunch moveit_steup_assistant setup_assistant.launch
```
7) Launch the Gazebo demo.
```
$ roslaunch moveit_pkg demo_gazebo.launch
```
8) Now, you'd have an output as so:

![output](https://raw.githubusercontent.com/MeshalAlamr/ros-robot-arm-control/main/output.gif)

You can move the robot arm in Rviz (left) then execute the planning as shown which will reflect on the Gazebo simulation (right).


