----------------------------------------------
# VMware Tools Download
----------------------------------------------
```
sudo apt-get install open-vm-tools-desktop -y
```
----------------------------------------------


----------------------------------------------
# VMware shrink
----------------------------------------------
```
sudo vmware-toolbox-cmd disk shrink /
```
----------------------------------------------


----------------------------------------------
# Easy bashrc
----------------------------------------------
```
# ////////////////| Easy Bash |///////////////
alias eb='nano ~/.bashrc'
alias editb='gedit ~/.bashrc'
alias sb='source ~/.bashrc'
alias gs='git status'
alias gp='git pull'
alias open="xdg-open"
alias cm="catkin_make"
alias ds='cd $wsldir'
alias rs='cd $wsldir/resources'

# ////////////////| Easy Diractory |//////////
wsldir="/mnt/d/WSL"
alias slam='cd $wsldir/lider_slams'

alias fastlio2='cd $wsldir/lider_slams/fastlio2/'
alias fasterlio='cd $wsldir/lider_slams/fasterlio/'
alias legoloam='cd $wsldir/lider_slams/legoloam/'
alias liosam='cd $wsldir/lider_slams/liosam/'
alias cticp='cd $wsldir/lider_slams/cticp/'
alias pointlio='cd $wsldir/lider_slams/pointlio/'
alias udataset='cd $wsldir/usharing/usharing_private/'
alias dataset='cd $wsldir/usharing/'

alias spointlio='source /mnt/d/WSL/lider_slams/pointlio/devel/setup.bash'
alias sfasterlio='source /mnt/d/WSL/lider_slams/fasterlio/devel/setup.bash'
alias sfastlio2='source /mnt/d/WSL/lider_slams/fastlio2/devel/setup.bash'
alias sliosam='source /mnt/d/WSL/lider_slams/liosam/devel/setup.bash'
alias slegoloam='source /mnt/d/WSL/lider_slams/legoloam/devel/setup.bash'

# ////////////////| ROS DIR |/////////////////
source /opt/ros/noetic/setup.bash
source /mnt/d/WSL/resources/ws_livox/devel/setup.bash

# ////////////////| The End |/////////////////


localhostipv4=`ifconfig | grep 192 | awk -F " " '{print $2}'`
export ROS_MASTER_URI=http://$localhostipv4:11311
export ROS_HOSTNAME=$localhostipv4
export TURTLEBOT3_MODEL=burger
```
----------------------------------------------


----------------------------------------------
# fast-lio
----------------------------------------------
```
sudo apt-get install -y libgoogle-glog-dev
sudo apt-get install -y libeigen3-dev
sudo apt-get install -y libpcl-dev
sudo apt-get install -y libyaml-cpp-dev
```
----------------------------------------------


----------------------------------------------
# WSL
----------------------------------------------
```
wsl --install Ubuntu-20.04
wsl --set-default-version 2
wsl --update
```
----------------------------------------------


----------------------------------------------
# Vscode Configurations
----------------------------------------------
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
----------------------------------------------


----------------------------------------------
# Save map
----------------------------------------------
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
----------------------------------------------


----------------------------------------------
# CMakeLists for cpp
----------------------------------------------
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
----------------------------------------------


----------------------------------------------
CMakeList.txt
----------------------------------------------
```
CMakeLists.txt 
cmake_minimum_required(VERSION 3.16.3)
project(HelloSLAM)
set(CMAKE_BUILD_TYPE "Debug")
add_executable(a hello.cpp)

# add_library(hello libHelloSLAM.cpp)
# add_library(hello_shared SHARED libHelloSLAM.cpp)

# add_executable(useHello useHello.cpp)
# target_link_libraries(useHello hello_shared)
```
----------------------------------------------
----------------------------------------------
----------------------------------------------


----------------------------------------------
----------------------------------------------
----------------------------------------------


----------------------------------------------
----------------------------------------------
----------------------------------------------


--------------------The End-------------------
