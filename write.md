Install wsl, docker, vs code
Create new project from the embedded system team
After that, cd PlatformIO/{project name}
Input `docker pull osrf/ros:foxy-desktop` to install foxy
Input `docker run -it --net=host --name my_foxy_container osrf/ros:foxy-desktop` to create container in docker
(Input `docker exec -it my_foxy_container bash` to acess the container)
(Input `echo $ROS_DISTRO` to know its in foxy version)
Input `echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc` to save the setup into environment
Source the Workspace and Launch the Simulation
```bash  sudo apt-get install ros-foxy-joint-trajectory-controller
sudo apt-get install ros-foxy-controller-manager
sudo apt-get install ros-foxy-trajectory-msgs
sudo apt-get install ros-foxy-gazebo-ros2-control*
sudo apt-get install ros-foxy-joint-state-controller
sudo apt-get install ros-foxy-position-controllers
```
Install related software packages
```bash
sudo apt-get install build-essential libgtk-3-dev
sudo apt install python3-pip
sudo pip3 install wxpython
sudo pip3 install transforms3d
```
If the "sudo pip3 install wxpython" can't work, you can use: `sudo apt-get install python3-wxgtk4.0`
Install or upgrade MoveIt
```bash
sudo apt-get update
sudo apt-get install ros-foxy-moveit
```
Install this repository from Source
```bash
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
sudo apt install git
git clone -b foxy_ethercat https://github.com/YWT-st/elfin_robot_ros2.git
cd ..
colcon build
source install/setup.bash
```

```bash
# 步驟 1
apt-get update && apt-get install -y lxde lxworkspace-dev x11vnc xvfb vlc

# 步驟 2
apt-get install -y git python3-pip
git clone https://github.com/novnc/noVNC.git /opt/noVNC
git clone https://github.com/novnc/noVNC.git /opt/noVNC/utils/websockify

# 步驟 3
Xvfb :1 -screen 0 1280x800x24 &
export DISPLAY=:1
startlxde &
x11vnc -forever -shared -display :1 -nopw &
/opt/noVNC/utils/novnc_proxy --vnc localhost:5900 --listen 6080 &
```

Usage with Gazebo Simulation
1. Launch Gazebo & RViz (with MoveIt!) `ros2 launch elfin5_ros2_moveit2 elfin5.launch.py`
2. Start API & Control Panel
```bash
ros2 launch elfin5_ros2_moveit2 elfin5_basic_api.launch.py
ros2 launch elfin_basic_api fake_elfin_gui.launch.py
```



