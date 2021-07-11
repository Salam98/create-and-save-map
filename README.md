# create-and-save-map

Task 1 with turtulebot3



Install TurtleBot3 Packages:


$ sudo apt-get install ros-melodic-dynamixel-sdk

$ sudo apt-get install ros-melodic-turtlebot3-msgs

$ sudo apt-get install ros-melodic-turtlebot3


Set TurtleBot3 Model Name:


$ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc



Install Simulation Package:



$ cd ~/catkin_ws/src/

$ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git

$ cd ~/catkin_ws && catkin_make


Launch Simulation World:

1-	Empty World

$ export TURTLEBOT3_MODEL=waffle_pi

$ roslaunch turtlebot3_gazebo turtlebot3_empty_world.launch


## I got this error:

Resource not found: turtlebot3_description

ROS path [0]=/opt/ros/melodic/share/ros

ROS path [1]=/home/salam/catkin_ws/src

ROS path [2]=/opt/ros/melodic/share

The traceback for the exception was written to the log file


#so to solve these problem I installed (turtlebot3_description) by the command:

$ sudo apt-get install ros-melodic-turtlebot3-description



2-	TurtleBot3 World:

$ export TURTLEBOT3_MODEL=waffle_pi

$ roslaunch turtlebot3_gazebo turtlebot3_world.launch


![world](https://user-images.githubusercontent.com/85636030/125210427-7a597c00-e2a8-11eb-8a73-ae91e6655f59.png)




Run SLAM Node:


$ export TURTLEBOT3_MODEL= waffle_pi

$ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping


(make sure gampping pkg installed  "sudo apt-get install ros-melodic-gmapping" )



![slam](https://user-images.githubusercontent.com/85636030/125210464-a5dc6680-e2a8-11eb-97e7-5a958a40f091.png)



Operate TurtleBot3:


$ roslaunch turtlebot3_gazebo turtlebot3_simulation.launch


![mapping](https://user-images.githubusercontent.com/85636030/125210489-ce646080-e2a8-11eb-80ad-6b7652c74eb1.png)


Save Map:


Wait until all the map explored then save it by the command :

$ rosrun map_server map_saver -f ~/map


(make sure map_server pkg installed  "sudo apt-get install ros-melodic-map_server" )


##I got this error when I tried to install map_server pkg  :


The following packages have unmet dependencies: ros-melodic-map-server : 

Depends: libsdl-image1.2-dev but it is not going to be installed

Depends: libsdl1.2-dev but it is not going to be installed

E: Unable to correct problems, you have held broken packages.


#Solution:

Open software & updates and set the three options on as it shown below


![s u](https://user-images.githubusercontent.com/85636030/125210564-3adf5f80-e2a9-11eb-97ce-b85282222598.png)


After this step map_server pkg has installed sucssufully 


![complete](https://user-images.githubusercontent.com/85636030/125210586-59455b00-e2a9-11eb-9d60-07b9ebd2b0bc.png)




TASK 2 with another ros robot 


From: https://githubmemory.com/repo/zyvoi/Udacity-Robotics-SLAM


First I installed  'RTAB-Map ROS' dependency :


$ sudo apt install ros-melodic-rtabmap-ros


second build the instruction :


$ cd  ~/catkin_ws/src

$ git clone https://github.com/dudasdavid/Udacity-Robotics-SLAM

$ cd ~/catkin_ws && catkin_make

$ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc


Launching robot world:

$ roslaunch my_robot world.launch


![launch_world](https://user-images.githubusercontent.com/85636030/125210709-35cee000-e2aa-11eb-8d73-29f28b0d9efc.png)


$ roslaunch my_robot mapping.launch

$ roslaunch my_robot teleop.launch



After mapping 


![after_mapping](https://user-images.githubusercontent.com/85636030/125210737-5ac35300-e2aa-11eb-9ebe-b90af25906f8.png)



Save Map :

$ rosrun map_server map_saver -f ~/map



![save_map](https://user-images.githubusercontent.com/85636030/125210786-9827e080-e2aa-11eb-8672-22d112e2c046.png)










