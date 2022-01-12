# cartographer_and_qrcode

## 1. Installation

### 1.1. enviroment install

We have tested cartographer_ros on machines with the following configurations

* Ubuntu 18.04.6 LTS + ROS melodic

ros melodic install refer:http://wiki.ros.org/melodic/Installation/Ubuntu

### 1.2. source code install

	$ sudo apt-get update
	$ sudo apt-get install -y python-wstool python-rosdep ninja-build stow

	$ mkdir catkin_ws
	$ cd catkin_ws
	$ wstool init src
	$ wstool merge -t src https://raw.githubusercontent.com/cartographer-project/cartographer_ros/master/cartographer_ros.rosinstall
	$ wstool update -t src

	$ sudo rosdep init
	$ rosdep update
	$ rosdep install --from-paths src --ignore-src --rosdistro=melodic -y

	$ src/cartographer/scripts/install_abseil.sh

	$ sudo apt-get remove ros-melodic-abseil-cpp

	$ cd ~/catkin_ws/src 
	$ rm -rf cartographer_ros/
	$ git clone https://github.com/AIRS-TJ/cartographer_and_qrcode.git
	$ sudo apt-get install ros-melodic-map-server
	$ cd ..
	$ catkin_make_isolated --install --use-ninja

## 2. Usage

**编译:**

	$ cd ~/catkin_ws/

	$ catkin_make_isolated --install --use-ninja 

注意：任何文件只要修改了内容就需要重新编译，即使修改的launch文件或配置都需要重新编译

**运行之前souce环境变量：**

	$ cd ~/catkin_ws/
	
	$ source install_isolated/setup.bash

**运行:**

打开有二维码的gazebo环境:

	$ gedit ~/.bashrc 
export TURTLEBOT3_MODEL=waffle_pi

(说明：waffle_pi有摄像头)

	$ roslaunch turtlebot3_gazebo turtlebot3_warehouse.launch

打开遥控：

	$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

打开turtlebot3的visp_auto_tracker:

	$ roslaunch visp_auto_tracker turtlebot3.launch 

打开cartographer和rviz:

	$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=cartographer

