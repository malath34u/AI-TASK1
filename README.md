# 1 PC Setup

## 1.1  Install ROS 1 on Remote PC
* `$ sudo apt-get upgrade`
* `$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh`
* `$ chmod 755 ./install_ros_kinetic.sh `
* `$ bash ./install_ros_kinetic.sh`

## 1.2  Install Dependent ROS 1 Packages
* `$ sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy \
  ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc \
  ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan \
  ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python \
  ros-kinetic-rosserial-server ros-kinetic-rosserial-client \
  ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server \
  ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro \
  ros-kinetic-compressed-image-transport ros-kinetic-rqt* \
  ros-kinetic-gmapping ros-kinetic-navigation ros-kinetic-interactive-markers`

## 1.3  Install TurtleBot3 Packages
* `$ sudo apt-get install ros-kinetic-dynamixel-sdk`
* `$ sudo apt-get install ros-kinetic-turtlebot3-msgs`
* `$ sudo apt-get install ros-kinetic-turtlebot3`

## 1.4  Set TurtleBot3 Model Name

### 1.4.1 In case of TurtleBot3 Burge
* `$ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc`
### 1.4.2 In case of TurtleBot3 Waffle Pi 
* `$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc`

# 2 Simulation

## 2.1 Gazebo Simulation
### 2.1.1 Install Simulation Package
* `$ cd ~/catkin_ws/src/`
* `$ git clone -b kinetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git`
* `$ cd ~/catkin_ws && catkin_make`

### 2.1.2 Launch Simulation World

#### 2.1.2.1 Empty World
![Picture 1](https://b.top4top.io/p_2060wyiqb1.png)
* `$ export TURTLEBOT3_MODEL=burger`
* `$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch`

#### 2.1.2.2 TurtleBot3 World
![Picture 2](https://i.top4top.io/p_2027hse291.png)
* `$ export TURTLEBOT3_MODEL=waffle`
* `$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`

## 2.2 SLAM Simulation

### 2.2.1 Launch Simulation World
* `$ export TURTLEBOT3_MODEL=burger`
* `$ roslaunch turtlebot3_gazebo turtlebot3_world.launch`

![Picture 2](https://c.top4top.io/p_2060m0mlt2.png)

### 2.2.2 Run SLAM Node
* `$ export TURTLEBOT3_MODEL=burger`
* `$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping`
![Picture 3](https://d.top4top.io/p_2060t24jx3.jpg)

### 2.2.3 Run Teleoperation Node
* `$ export TURTLEBOT3_MODEL=burger`
* `$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch`
![Picture 4](https://e.top4top.io/p_2060a8hq34.png)

### 2.2.4 Save Map
* `$ rosrun map_server map_saver -f ~/map`

![Picture 3](https://d.top4top.io/p_2060t24jx3.jpg)
