This repository contains both the ROS2 code and a guide for connecting to and operating the baby bot (bbot). I *highly* recommend reading the documentation at https://docs.ros.org/en/humble/Tutorials.html (at least up to and including the header *Writing a simple service and client*) before continuing.

# Setup
### Connecting to the Pi
- Ensure that the Pi and your device are connected to the same network. This network must also be one in which the two devices can see (ping) each other. By default, the Pi contains a startup script which will automatically connect it to the router's network (SSID `Team36`, password `UPRobotics!`). 
- Now you can SSH into the Pi from your device:
	- Acquire the Pi's IP address. The Pi is configured to use the static IP address `192.168.0.7` when connected to the the router. If It's not on the router, you'll have to acquire its IPV4 address by typing `iwconfig -a` into the console on the Pi.
	- On Ubuntu, type `ssh upmoon25@192.168.0.7` into the console. The password is `upmoon25`. 
	- On Windows, idk :( if someone could add to this that'd be great
### Running the code in this repository
I plan on adding bash scripts to this repository to streamline this process. For now, the following instructions will work:
- Ensure ROS2 Humble is installed on the machine you're running the code on. Of course, the Pi already has ROS2 Humble setup. There's an installation tutorial [here](https://docs.ros.org/en/humble/Installation.html). **Make sure your domain ID is set to 8888!** 
- `cd` into the root of the workspace (the folder containing all the packages).
- In your console, type the following commands:
	- `colcon build --packages-select package_name`
	- `source install/local_setup.bash`
	- `ros2 run package_name node_name`
- So, for example, if you wanted to run the `keyboard_subscriber` node on the Pi, which is in the `bbot` package, you would run
	- `colcon build --packages-select bbot`
	- `source install/local_setup.bash`
	- `ros2 run bbot keyboard_subscriber`
