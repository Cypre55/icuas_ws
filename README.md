# ICUAS Workspace

This repository is Team ARL-KGP's solution for the [ICUAS UAV Competition 2022](http://www.uasconferences.com/2022_icuas/uav-competition-rulebook-and-faq/).

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

### How to Clone

This repository should be cloned into a catkin workspace using the following command

```bash
git clone --recurse-submodules -j8 https://github.com/Cypre55/icuas_ws.git
```

Please follow instructions specified in each submodule.

