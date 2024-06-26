# motor_controller_pkg
This ROS package contains a motor_controller node that subscribes to motor control commands and performs basic functionalities such as starting, stopping, and setting velocity.

## Prerequisites
* ROS (Robot Operating System) installed. You can install ROS by following the instructions [here](https://wiki.ros.org/melodic/Installation/Ubuntu).

## Building the Package
To build the motor_controller_pkg package, follow these steps:

1. Build Catkin Workspace:
```
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/src
catkin_init_workspace
```
2. Clone this repository into your catkin workspace's src directory:
```
git clone https://github.com/YamaAndrew/Assignment-1.git
```
3. Build the package in the catkin_ws:
```
cd ..
catkin_make -j4
```
4. Start a rosmaster
```
roscore
```

## Running the motor_controller Node
**Open a new terminal.** Run the motor_controller node using the following steps:

1. Make sure your ROS environment is set up properly by sourcing your workspace:
```
source /path/to/your/catkin_workspace/devel/setup.bash
```
Replace /path/to/your/catkin_workspace with the actual path to your catkin workspace.
2. Launch the motor_controller node using rosrun:
```
rosrun motor_controller_pkg motor_controller
```

## Testing the Node
**Open a new terminal.** Make sure your ROS environment is set up properly by sourcing your workspace:
```
source /path/to/your/catkin_workspace/devel/setup.bash
```
Now you can publish messages to the /motor_commands topic using the rostopic pub command. For example:

To start the motor:
```
rostopic pub /motor_commands motor_controller_pkg/MotorCommand "command: 'start'"
```
To stop the motor:
```
rostopic pub /motor_commands motor_controller_pkg/MotorCommand "command: 'stop'"
```
To set the velocity to a specific value (e.g., 1.5):
```
rostopic pub /motor_commands motor_controller_pkg/MotorCommand "command: 'velocity', velocity: 1.5"
```

## Message Format
The motor_controller node expects messages of type MotorCommand on the /motor_commands topic. The MotorCommand message has the following format:
```
# Command: "start", "stop", "velocity"
string command
# Velocity value
float32 velocity
```


