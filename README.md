# ICUAS Workspace

This repository is Team ARL-KGP's solution for the [ICUAS UAV Competition 2022](http://www.uasconferences.com/2022_icuas/uav-competition-rulebook-and-faq/).

The solution works on ROS Noetic and tested with Pop! OS 20.04 (Debian-based) 

It contains the following submodules:

```bash
├── README.md
└── src
    ├── ar_track_alvar
    ├── FUEL
    ├── icuas22_competition
    ├── larics_gazebo_worlds *
    ├── storm_gazebo_ros_magnet *
    └── uav_ros_simulation *

* - Given by the organisers
Rest are a part of our solution
```

The above configuration helped each sub-team to work on independent repositories. It also enabled simple setup for end-to-end testing across various machines.

Feel free to raise an issue if any of the following steps does not work.

### How to Clone

This repository should be cloned into a catkin workspace (say icuas_ws) using the following command

```bash
git clone --recurse-submodules -j8 https://github.com/Cypre55/icuas_ws.git
```

### Setup

##### UAV ROS Simulation

```bash
# Setting up UAV ROS Simulation
cd icuas_ws/src/uav_ros_simulation
./installation/install.sh
```

##### .bashrc/.zshrc

```bash
# Append the following to .bashrc

source ~/arl_kgp_ws/devel/setup.bash
# Shell script configuration
source ~/arl_kgp_ws/src/uav_ros_simulation/ros_packages/uav_ros_stack/miscellaneous/shell_additions/shell_scripts.sh
source ~/arl_kgp_ws/src/uav_ros_simulation/.gitman/ardupilot/Tools/completion/completion.bash
# Ardupilot exports
export PATH=$PATH:~/arl_kgp_ws/src/uav_ros_simulation/firmware/ardupilot/Tools/autotest
export PATH=/usr/lib/ccache:$PATH
source /usr/share/gazebo/setup.sh
source ~/arl_kgp_ws/src/uav_ros_simulation/firmware/ardupilot/Tools/completion/completion.bash
export PATH=~/.local/bin:$PATH
export GAZEBO_PLUGIN_PATH=$GAZEBO_PLUGIN_PATH:~/arl_kgp_ws/build/ardupilot_gazebo

#########################################################
# If you use zsh

source ~/arl_kgp_ws/devel/setup.zsh
# Shell script configuration
source ~/arl_kgp_ws/src/uav_ros_simulation/ros_packages/uav_ros_stack/miscellaneous/shell_additions/shell_scripts.sh
source ~/arl_kgp_ws/src/uav_ros_simulation/.gitman/ardupilot/Tools/completion/completion.zsh
# Ardupilot exports
export PATH=$PATH:~/arl_kgp_ws/src/uav_ros_simulation/firmware/ardupilot/Tools/autotest
export PATH=/usr/lib/ccache:$PATH
source /usr/share/gazebo/setup.sh
source ~/arl_kgp_ws/src/uav_ros_simulation/firmware/ardupilot/Tools/completion/completion.zsh
export PATH=~/.local/bin:$PATH
export GAZEBO_PLUGIN_PATH=$GAZEBO_PLUGIN_PATH:~/arl_kgp_ws/build/ardupilot_gazebo
```

##### Dependencies

```bash
sudo apt-get install libarmadillo-dev ros-noetic-nlopt libdw-dev

# Solution doesn't work with ros-noetic-nlopt 
# Using the static object from ros-melodic-nlopt 
# Replace the libnlopt_cxx.so.0.7.0 at /opt/ros/noetic/lib with the one in this folder
sudo cp ~/arl_kgp_ws/libnlopt_cxx.so.0.7.0 /opt/ros/noetic/lib/
```

##### Build

```bash
catkin config --cmake-args -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_STANDARD=17
catkin build #(Multiple time, till successful)
```

### Run

To run use the following command:

```bash
rosrun start.sh <World Number (1-5)>
```
