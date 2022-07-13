# Virtual-Box-Ubuntu-install-of-ROS-Noetic-

### This Repository will a step by step guide to install ROS on Ubuntu Linux using Virtual box.

#### First we need to install Virtual Box in order to run a Linux on a virtual machine using Ubuntu.
  VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use. 
  To download VirtualBox head to [VirtualBox.org](https://www.virtualbox.org/wiki/Downloads) and choose the latest version for your operating system.
  
  ![VB Download](https://user-images.githubusercontent.com/98822141/178605696-9bfdbc11-e3e6-4c81-9535-97023f201dc2.png)

  Then all you need to do is follow along with the set up wizard to install VirtualBox, when you are done you should be able to run it and see this window, without any virtual machines of course.
  
  ![VB UI](https://user-images.githubusercontent.com/98822141/178605030-755a38e7-6766-4f62-8a13-5cdb147af0d8.png)
  
#### Now to Download Ubuntu and and create a virtual machine running Linux.
First you need to visit [Ubuntu.com](https://ubuntu.com) then go to the downloads page, choose Ubuntu desktop and select your desired version, your choosen version will determine which ROS version you can install, we will discuss that later when we get to installing ROS, I will be wroking on Ubuntu 20.04
Note that it's recommended to isntall an LTS version, which stands for long term support.
After you finish downloading the Ubuntu ISO file we can start installing it on VirtualBox.
Start VirtualBox, then hit the **NEW** button, fill in your machine name, type and version and then click next, as shown below:

![Ubuntu#1](https://user-images.githubusercontent.com/98822141/178610816-f41165b2-b8e7-4b20-a305-7c51da278aca.png)

The Next Few pages will have set up the specifications for your new virtual machine. follow the images below: 

![Ubuntu#2](https://user-images.githubusercontent.com/98822141/178611715-dc037f35-e7b8-4272-9cae-9d8ab34ebfab.png)

![Ubuntu#3](https://user-images.githubusercontent.com/98822141/178611732-ac2f11e5-189a-4b1d-8f69-8af2164a750b.png)

![ubuntu#4](https://user-images.githubusercontent.com/98822141/178611738-797ae9e8-5651-4722-99de-d1b83c05acf7.png)

![ubuntu#5](https://user-images.githubusercontent.com/98822141/178611753-475d1d84-7841-40c9-b426-84b5847e5710.png)

![ubuntu#6](https://user-images.githubusercontent.com/98822141/178611766-680e6f0c-637e-4c17-b74f-e4588743da3e.png)

After you are done click on create, now your virtual machine should appear on your VirtualBox manager, select it and click on settings to customize and set up your machine before launching it.
These settings can vary from one device to another, and prefrence may play part in some of it, here is my recommended settings:

![ubuntu#7](https://user-images.githubusercontent.com/98822141/178626355-68e74332-e8b8-445a-b1cf-daff2001b353.png)

![ubuntu#8](https://user-images.githubusercontent.com/98822141/178626369-f64841bd-7f91-4bbf-98cf-7a4958fbad68.png)

![ubuntu#9](https://user-images.githubusercontent.com/98822141/178626376-ffefdff7-9e7d-4478-bc0e-05fbaedde7f6.png)

Anything that is not shown can be left as default

And now to add the ISO file that we downloaded from Ubuntu, from settings select **Storage**, and under **Storage Devices** under **Controller: IDE** click on the empty disc, go to **Attributes** and click on the disc icon next to **Optical drive:**, then select **Choose a dick file**, then go to where you downloaded your ISO file and select it.
Now your virtual machine is ready, exit settings, select your virtual machine and click on **Start**.
Now your vitrual machine should be running, for your first time you will need to isntall and set up Ubuntu to run on it.
After waitting for a bit an isntall window should pop up, select your language and click **Install Ubuntu**

![ubuntu#11](https://user-images.githubusercontent.com/98822141/178629008-6407ffb9-b351-49b9-b71e-ea995952c394.png)

Choose your keyboard layout

![ubuntu#12](https://user-images.githubusercontent.com/98822141/178629087-d7b5dbf6-a9b8-4203-8d55-53e10d2979fa.png)

In the next page make sure to check the last 2 boxes

![Ubuntu#13](https://user-images.githubusercontent.com/98822141/178629166-d9d435a9-6de0-4385-97bc-d6b8f18b83b5.png)

Finally keep this page as it is and click **Install Now**

![Ubuntu#14](https://user-images.githubusercontent.com/98822141/178629223-c2eff877-dcc7-429e-9989-ebfbc7cea20e.png)

Now you can continue by selecting your time zone, filling in your name and password, when you are done click **Continue** and Ubuntu should start installing.
After sometime your installing  will be complete and Ubuntu will require you to restart your virtual machine, click **Restart** and after restarting you should be able to use Linux on your virtual machine as you please.

#### Finally installing ROS on Linux.
Installing ROS will be stright forward, but first of all as we mentioned earlier, the version of ROS you will be installing depends on what version of Ubuntu you have
For Ubuntu 20.04 download ROS Noetic
For Ubuntu 18.04 download ROS Melodic
For Ubuntu 16.04 download ROS kinetic

To install ROS go to your Linux terminal in your virtual machine, and once at a time enter these commands:
Setup your computer to accept software from packages.ros.org.
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
Set up your keys
```
sudo apt install curl 
curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
To make sure your Debian package index is up-to-date
```
sudo apt update
```
Installing ROS Noetic
```
sudo apt install ros-noetic-desktop-full
```
Environment setup
```echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc

source ~/.bashrc

sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential

sudo apt install python3-rosdep

sudo rosdep init

rosdep update

mkdir -p ~/catkin_ws/src

cd ~/catkin_ws/

catkin_make

cd ~/catkin_ws/src
```
Now to add a project, we will clone a robot arm project from Smart-Methods.
```
git clone https://github.com/smart-methods/arduino_robot_arm.git 

cd ~/catkin_ws

rosdep install --from-paths src --ignore-src -r -y

sudo apt-get install ros-noetic-moveit

sudo apt-get install ros-noetic-joint-state-publisher ros-noetic-joint-state-publisher-gui

sudo apt-get install ros-noetic-gazebo-ros-control joint-state-publisher

sudo apt-get install ros-noetic-ros-controllers ros-noetic-ros-control

catkin_make
```
Finally to launch Ros with the added project 
```
roslaunch robot_arm_pkg check_motors.launch

```
Note that you might encounter an erorr when launching a project, if you do try this command
```
source devel/setup.bash
```
Now everything should be working perfectly, enjoy!!
![Screenshot from 2022-07-13 00-36-59](https://user-images.githubusercontent.com/98822141/178635524-b9dd89a9-fe29-45c1-83ba-c3b717f41ebf.png)
