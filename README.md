# Where Am I Udacity Robotics ND

## Before Localization

![image](https://github.com/amrtariq/Project_3/blob/main/WhereAmI/src/my_robot/screenshots/1-%20init.png)

## After Localization

![image](https://github.com/amrtariq/Project_3/blob/main/WhereAmI/src/my_robot/screenshots/2-%20localized.png)


- Build Two Wheeled robot
- Use the Adaptive Monte Carlo Localization to localize Robot.

## Structure

```
    .Where AM I            # Where Am I Project
|ــ   
├ٌٍWhereAmI
├─ src
├── my_robot                               # my_robot package        
│   │   ├── config                         # config folder for configuration files   
│   │   │   ├── base_local_planner_params.yaml
│   │   │   ├── costmap_common_params.yaml
│   │   │   ├── global_costmap_params.yaml
│   │   │   ├── local_costmap_params.yaml
│   │   ├── launch                         # launch folder for launch files   
│   │   │   ├── amcl.launch
│   │   │   ├── robot_description.launch
│   │   │   ├── world.launch
│   │   ├── maps                           	   # maps folder for maps
│   │   │   ├── map.pgm
│   │   │   ├── map.yaml
│   │   ├── meshes                           # meshes folder for sensors
│   │   │   ├── hokuyo.dae
│   │   ├── Models                           # models folder for models files
│   │   │   ├── white_ball
│   │   │   │   ├── model.config
│   │   │   │   ├── model.sdf
│   │   │   ├── project2_building
│   │   │   │   ├── model.config
│   │   │   │   ├── model.sdf	              
│   │   ├── urdf                             # urdf folder for xarco files
│   │   │   ├── my_robot.gazebo
│   │   │   ├── my_robot.xacro
│   │   ├── worlds                         # world folder for world files
│   │   │   ├── empty.world
│   │   │   ├── myworld.world
│   │   │   ├── office.world	
│   │   ├── CMakeLists.txt                 # compiler instructions
│   │   ├── package.xml                    # package info
│   ├── pgm_map_creator                    # pgm_map_creator        
│   │   ├── launch                         # launch folder for launch files   
│   │   │   ├── request_publisher.launch
│   │   ├── maps                           # maps folder for generated maps
│   │   │   ├── mymap.pgm
│   │   │   ├── mymap.yaml
│   │   ├── msgs                           # msgs folder for communication files
│   │   │   ├── CMakeLists.txt
│   │   │   ├── collision_map_request.proto
│   │   ├── src                            # src folder for main function
│   │   │   ├── collision_map_creator.cc
│   │   │   ├── request_publisher.cc
│   │   ├── world                          # world folder for world file
│   │   │   ├── udacity_mtv
│   │   ├── CMakeLists.txt                 # compiler instructions
│   │   ├── LICENSE                        # License for repository
│   │   ├── README.md                      # README for documentation
│   │   ├── package.xml                    # package info
│   ├── teleop_twist_keyboard              # teleop_twist_keyboard
│   │   ├── CHANGELOG.rst                  # change log
│   │   ├── CMakeLists.txt                 # compiler instructions
│   │   ├── README.md                      # README for documentation
│   │   ├── package.xml                    # package info
│   │   ├── teleop_twist_keyboard.py       # keyboard controller
```
## Clone and Build

Step 1: Install Following Packages

```
$ sudo apt-get install ros-kinetic-navigation
$ sudo apt-get install ros-kinetic-map-server
$ sudo apt-get install ros-kinetic-move-base
$ sudo apt-get install ros-kinetic-amcl
```
The map ROS AMCL Package usesa pgm file. A pgm file is a grayscale image file that represents the MAP.
Step 2: Clone Repo Directly into your workspaces folder

Step 3: Install Dependencies

libignition-math2-dev and protobuf-compiler to compile the map creator:

```
sudo apt-get install libignition-math2-dev protobuf-compiler
```
Step 4: Build WS

```
$ cd ~(your Directory)/WhereAmI
$ catkin_make
```
## Run the project

Launch my_robot in Gazebo to load both the world and plugins

```
$ roslaunch my_robot world.launch
```
Launch amcl node
```
$ roslaunch my_robot amcl.launch
```

### Testing

You have two options to control your robot while it localize itself here:
- Send navigation goal via RViz
- Send move command via teleop package.


Navigate your robot, observe its performance and tune your parameters for AMCL.

### Option 1: Send 2D Navigation Goal

Your first option would be sending a 2D Nav Goal from RViz.
The move_base will try to navigate your robot based on the localization. Based on the new observation and the odometry, the robot to further perform the localization.
- Click the 2D Nav Goal button in the toolbar, then click and drag on the map to send the goal to the robot. 
- It will start moving and localize itself in the process. If you would like to give amcl node a nudge, you could give the robot an initial position estimate on the map using 2D Pose Estimate.

### Option 2: Use Teleop Node

You could also use teleop node to control your robot and observe it localize itself in the environment.
Open another terminal and launch the teleop script:
```
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
```
You could control your robot by keyboard commands now.

![WhereAmI](https://user-images.githubusercontent.com/18179768/156850586-b26128b0-fa51-4de3-b899-6253c7e3e52b.gif)
