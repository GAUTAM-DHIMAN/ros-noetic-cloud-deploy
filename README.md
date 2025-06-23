# ROS Noetic Cloud Deployment on AWS

This project shows how to deploy ROS Noetic on an AWS EC2 Ubuntu 20.04 LTS instance. It enables developers to run and test ROS remotely on the cloud.

## Instance Details

- OS: Ubuntu 20.04 LTS  
- EC2 Type: t3.micro  
- Storage: 30GB  
- Region: eu-north-1  
- Public IP: 13.53.144.71

## Installation Steps

1. Launch EC2 instance with Ubuntu 20.04 and configure security group (allow SSH).  
2. SSH into the instance:  
   ```bash
   ssh -i ~/.ssh/ros-key.pem ubuntu@13.53.144.71
3.Setup ROS repository and keys:
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt install curl -y
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
sudo apt update
4. Install ROS Noetic desktop full:
sudo apt install ros-noetic-desktop-full -y
5. Initialize and update rosdep:
sudo apt install python3-rosdep -y
sudo rosdep init
rosdep update
6. Source ROS environment:
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
source ~/.bashrc
7. Run ROS core:
roscore
