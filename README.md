# Turtlebot3-with-SLAM-approach 

to create a map in SLAM follow these steps:

launch a ROS with this command:
   $ roscore
  
open a new terminal and copy these commands:
   $ sudo apt update
   $ sudo apt upgrade
   $ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_melodic.sh
   $ chmod 755 ./install_ros_melodic.sh 
   $ bash ./install_ros_melodic.sh
   $ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
   ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
   ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
   ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
   ros-melodic-rosserial-server ros-melodic-rosserial-client \
   ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
   ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
   ros-melodic-compressed-image-transport ros-melodic-rqt* \
   ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers
   
Install TurtleBot3 Packages
   $ sudo apt-get install ros-melodic-dynamixel-sdk
   $ sudo apt-get install ros-melodic-turtlebot3-msgs
   $ sudo apt-get install ros-melodic-turtlebot3
  
Set TurtleBot3 Model Name:

In case of TurtleBot3 Burger
   $ echo "export TURTLEBOT3_MODEL=burger" >> ~/.bashrc
   
In case of TurtleBot3 Waffle Pi
   $ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
   
   
   
to open a Simulation open a new terminal and follow these steps:

Install Simulation Package:
   $ cd ~/catkin_ws/src/
   $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
   $ cd ~/catkin_ws && catkin_make

Launch Simulation World:
   $ export TURTLEBOT3_MODEL=waffle
   $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
   
   
for SLAM Simulation open new terminal and Launch Simulation World with these commands:
   $ export TURTLEBOT3_MODEL=waffle
   $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
   
to Run SLAM Node open new terminal and copy the commands:
   $ export TURTLEBOT3_MODEL=waffle
   $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
   
to Run Teleoperation Node open new terminal and copy the commands:
   $ export TURTLEBOT3_MODEL=waffle
   $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

to Control Your TurtleBot3 moving 
        w
   a    s    d
        x

 w/x : increase/decrease linear velocity
 a/d : increase/decrease angular velocity
 space key, s : force stop
 
 to save a map open new terminal and copy the commands:
    $rosrun map_server map_saver -f ~/map
