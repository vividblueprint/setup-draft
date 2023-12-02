# VMware Tools Download
```
sudo apt-get install open-vm-tools-desktop -y
```
# VMware shrink
```
sudo vmware-toolbox-cmd disk shrink /
```
# Easy bashrc
```
# ////////////////| Permissions | ////////////
alias sudochmodxall="sudo chmod +x *"
alias sudochmodx="sudo chmod +x"
alias chmodxall="chmod +x *"
alias chmodx="chmod +x"

# ////////////////| Easy Bash |///////////////
alias eb='nano ~/.bashrc'
alias editb='gedit ~/.bashrc'
alias sb='source ~/.bashrc'
alias gs='git status'
alias gp='git pull'
alias open='xdg-open'
alias cm='catkin_make'
alias vpn='~/Downloads/Clash\ for\ Windows-0.20.39-x64-linux/cfw'
alias readme='cd /media/shamim/Local\ Disk/VMwares && gedit ./README.md'

# ////////////////| Easy Directory |//////////
wsldir="~/catkin_ws"
alias rs="cd $wsldir/resources "
alias slam="cd $wsldir/lider_slams"
alias learning="cd $wsldir/learning"
alias slambook="cd $wsldir/learning/slambook2"
alias download="cd ~/Downloads"

# ////////////////| Easy Directory |//////////
alias fastlio2="cd $wsldir/lider_slams/fastlio2/"
alias fasterlio="cd $wsldir/lider_slams/fasterlio/"
alias legoloam="cd $wsldir/lider_slams/legoloam/"
alias liosam="cd $wsldir/lider_slams/liosam/"
alias pointlio="cd $wsldir/lider_slams/pointlio/"

# ////////////////| Easy Directory |//////////
alias udataset="cd /media/shamim/Local\ Disk/WSL/usharing/usharing_private/"
alias dataset="cd /media/shamim/Local\ Disk/WSL/usharing/"

# ////////////////| Source SLAM |//////////
alias spointlio="source $wsldir/lider_slams/pointlio/devel/setup.bash"
alias sfasterlio="source $wsldir/lider_slams/fasterlio/devel/setup.bash"
alias sfastlio2="source $wsldir/lider_slams/fastlio2/devel/setup.bash"
alias sliosam="source $wsldir/lider_slams/liosam/devel/setup.bash"
alias slegoloam="source $wsldir/lider_slams/legoloam/devel/setup.bash"

# ////////////////| Source ROS |/////////////////
source /opt/ros/noetic/setup.bash
source ~/catkin_ws/resources/ws_livox/devel/setup.bash

# ////////////////| ROS export |/////////////////
# export ROS_MASTER_URI=http://10.128.21.70:11311
# export ROS_HOSTNAME=10.128.21.70
# alias burger="export TURTLEBOT3_MODEL=burger"

localhostipv4=`ifconfig | grep 192.168 | awk -F " " '{print $2}'`
export ROS_MASTER_URI=http://$localhostipv4:11311
export ROS_HOSTNAME=$localhostipv4
export TURTLEBOT3_MODEL=burger

# ////////////////| The End |/////////////////
```
# WSL
```
wsl --install Ubuntu-20.04
wsl --set-default-version 2
wsl --update
```
# Vscode Configurations
```
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "/opt/ros/noetic/include/",
                "/usr/include/pcl-1.10",
                "/usr/include/eigen3"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c17",
            "cppStandard": "gnu++14",
            "intelliSenseMode": "gcc-x64"
        }
    ],
    "version": 4
}
```
# Save map
```
//Shamim //infront
std::ofstream OpenFile;
const std::string file_path = "/home/ubuntu/yx_data/yx_slam_data/1_fastlio2_traj.txt";
//
    //Shamim       in main()
    OpenFile.open(file_path);
    //

    //Shamim		//in publish_odometry() after pubOdomAftMapped.publish(odomAftMapped);
    OpenFile<< std::fixed << setprecision(8) << odomAftMapped.header.stamp.toSec() << " " << setprecision(6) << odomAftMapped.pose.pose.position.x << " " << odomAftMapped.pose.pose.position.y << " " << odomAftMapped.pose.pose.position.z << " " << odomAftMapped.pose.pose.orientation.x << " " << odomAftMapped.pose.pose.orientation.y
    << " " <<odomAftMapped.pose.pose.orientation.z << " " << odomAftMapped.pose.pose.orientation.w <<std::endl;

    if(!ros::ok())
    {
        OpenFile.close();
    }
    //
```

# CMakeList.txt
```
cmake_minimum_required(VERSION 3.16.3)
project(HelloSLAM)
set(CMAKE_BUILD_TYPE "Debug")
add_executable(a hello.cpp)

# add_library(hello libHelloSLAM.cpp)
# add_library(hello_shared SHARED libHelloSLAM.cpp)
# target_link_libraries(useHello hello_shared)
```
# c++ compile.bash 
```
#!/bin/bash

# Bold
BBlack='\033[1;30m'       # Black
BRed='\033[1;31m'         # Red
BGreen='\033[1;32m'       # Green
BYellow='\033[1;33m'      # Yellow
BBlue='\033[1;34m'        # Blue
BPurple='\033[1;35m'      # Purple
BCyan='\033[1;36m'        # Cyan
BWhite='\033[1;37m'       # White

# Underline
UBlack='\033[4;30m'       # Black
URed='\033[4;31m'         # Red
UGreen='\033[4;32m'       # Green
UYellow='\033[4;33m'      # Yellow
UBlue='\033[4;34m'        # Blue
UPurple='\033[4;35m'      # Purple
UCyan='\033[4;36m'        # Cyan
UWhite='\033[4;37m'       # White
NC='\033[0m' # No Color

echo -e "${UCyan}${BCyan}          ${NC}${BCyan}Today is :" `date`"${UCyan}           "

echo -e "${UPurple}${BPurple}                          building                          ${NC}"
cmake -B build

echo -e "${UPurple}${BPurple}                            make                            ${NC}"
cd ./build/ && make -j16

echo -e "${UPurple}${BPurple}                          runing a                          ${NC}${BYellow}"
./a

echo -e "${UWhite}                           The End                          "
```
# linux solution
- ### Minimize window click-action
```
gsettings set org.gnome.shell.extensions.dash-to-dock click-action "minimize"
```
- ### scan device from the same network
```
sudo apt-get install nmap
ip route | grep default
nmap -sn xx.xx.xx.xx/24
```
# Remove Ubuntu from your dual boot system
1. Delete the drive where Ubuntu installed.
2. Log in to Windows 10/11 and insert these commands to the terminal:
```
 list disk
 
 select disk 0

 list partition

 select partition 1 # System

 assign letter=z

 exit

 z:

 dir

 cd efi

 dir

 rd ubuntu /s # remove ubuntu
 
 dir
```
# rosdep init update
```
151.101.84.133 raw.githubusercontent.com
```
---------------------------------------
