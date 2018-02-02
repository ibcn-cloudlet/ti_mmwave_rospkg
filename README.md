# ROS driver for TI mmwave sensor boards

This repo contains the ROS driver for TI mmwave sensor boards based on the [driver released by TI](http://dev.ti.com/tirex/content/mmwave_training_1_6_1/labs/lab0006-ros-driver/lab0006_ros_driver_pjt/TI_mmWave_ROS_Driver_Setup_Guide.pdf) 

These instructions are for the TI mmWave 1443 EVM board.

## Installation

These instructions are tested on Ubuntu 16.04. Make sure you have ROS installed (recommended version ROS kinetic). On Ubuntu this can be installed from the package manager.

This driver also requires PCL ROS. If not installed, install on Ubuntu with:

```
sudo apt-get install ros-kinetic-pcl-ros ros-kinetic-pcl-msgs ros-kinetic-pcl-conversions ros-kinetic-perception-pcl
```

Create a catkin ws

```
mkdir catkin_ws
cd catkin_ws
mkdir src
cd src
catkin_init_workspace
```

Clone the required repositories

```
git clone https://github.com/wjwwood/serial.git
git clone https://github.com/ibcn-cloudlet/ti_mmwave_rospkg.git
```

Now build the projects

```
cd ..  // go to workspace dir, catkin_ws
catkin_make
```

Finally make sure to source the setup.bash file to setup the environment

```
source devel/setup.bash
```

## Run

The driver communicates to the sensor board via serial ports. Therefore, your user must be member of the `dialout` unx group.

```
sudo adduser <username> dialout
```

To launch the driver, use the following command:

for 3-D configuration with elevation info:
```
roslaunch ti_mmwave_rospkg rviz_1443_3d.launch
```

for 2-D configuration:
```
roslaunch ti_mmwave_rospkg rviz_1443_2d.launch
```

Make sure you have the latest version of the TI mmWave EVM demo firmware installed on your board.
