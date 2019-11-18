# HomeServiceRobot-Project
This is a gazebo and ros based home service project build upon popular ros nodes

## Installation

1. Clone this environment and download submodules
  ```
  git clone git@github.com:jensakut/HomeServiceRobot-Project.git
  git submodule init
  git submodule update
  ```
2. Install ROS kinetic as described here http://wiki.ros.org/kinetic/Installation
```
  sudo apt-get install xterm
  sudo apt install ros-melodic ros-melodic-navigation ros-melodic-openslam-gmapping

```
  source /opt/ros/melodic/setup.bash
  cd catkin_ws
  catkin build && source /opt/ros/melodic/setup.bash

  
```

## Launch Project

Make launch file executable and execute it

  ```
  cd workingdir/ShellScripts/
  chmod +x launch.sh
  ./launch.sh
  ```

## Overview about catkin workspace source directory

The repository contains both cloned submodules and self-programmed parts:

#### Submodules
- [gmapping](http://wiki.ros.org/gmapping) contains a slam algorithm and the gmapping_demo.launch file. It
builds a map of the environment based on laser range finder sensors or RGB-D cameras
- [turtlebot_teleop](http://wiki.ros.org/turtlebot_teleop) allows manual control of the robot using keyboard_teleop.launch file
- [turtlebot_rviz_launchers](http://wiki.ros.org/turtlebot_rviz_launchers) contains a preconfigured rviz workspace and the view_navigation.launch file
- [turtlebot_gazebo](http://wiki.ros.org/turtlebot_gazebo) deploys a turtlebot in a
gazebo environment using turtlebot_world.launch

#### custom parts
- World: This directory stores the gazebo world file and the map generated from SLAM.
- ShellScripts: stores the shell scripts.
- RvizConfig: stores the customized rviz configuration files.
- wall_follower: will store a wall_follower node that will autonomously drive the robot around to perform SLAM.
- pick_objects: a node that commands your robot to drive to the pickup and drop off zones.
- add_markers: a node that models the object with a marker in rviz.

    ├──                                # Official ROS packages
    |
    ├── slam_gmapping                  # gmapping_demo.launch file                   
    │   ├── gmapping
    │   ├── ...
    ├── turtlebot                      # keyboard_teleop.launch file
    │   ├── turtlebot_teleop
    │   ├── ...
    ├── turtlebot_interactions         # view_navigation.launch file      
    │   ├── turtlebot_rviz_launchers
    │   ├── ...
    ├── turtlebot_simulator            # turtlebot_world.launch file
    │   ├── turtlebot_gazebo
    │   ├── ...
    ├──                                # Custom packages
    |
    ├── World                          # world files
    │   ├── ...
    ├── ShellScripts                   # shell scripts files
    │   ├── ...
    ├──RvizConfig                      # rviz configuration files
    │   ├── ...
    ├──wall_follower                   # wall_follower C++ node
    │   ├── src/wall_follower.cpp
    │   ├── ...
    ├──pick_objects                    # pick_objects C++ node
    │   ├── src/pick_objects.cpp
    │   ├── ...
    ├──add_markers                     # add_marker C++ node
    │   ├── src/add_markers.cpp
    │   ├── ...
    └──
