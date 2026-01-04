# INHA-Soccer ⚽️
Hi 👋 We are Inha-United !
Inha-United is a team competing in the RoboCup Soccer Humanoid League.

This repository provides a comprehensive set of algorithms and methodologies required for a robot to autonomously perform a soccer game.

Starting from the demo provided by Booster Robotics, we have modularized the system, extended its functionality, and continuously improved its performance through our own research and development efforts.

## vision 📷

The vision pipeline of this system is based on a YOLOv8 object detection model and performs high-speed inference through TensorRT optimization.
For the detected ball, line markers, and robot objects, the system applies a camera model and geometric transformations to convert the detection results into positions in the robot coordinate frame.

## brain 🧠

The Brain module consists of the following three core functionalities.

### 1. Behavior
Based on a BehaviorTree framework, various behaviors required to perform a soccer game are implemented in a modular manner. These behaviors are composed to form a pipeline that controls the overall game flow.

###	2. Localization
Localization algorithms are implemented to estimate the robot’s position and orientation on the field, using information provided by the Vision module.

###	3. Communication
The module processes information exchanged between team robots as well as game state data from the Game Controller, and integrates this information with the Behavior module to enable advanced team strategies and decision-making.

## game_controller 🎮
The system receives game control data transmitted via the UDP protocol from the Game Controller, converts it into ROS2 topic messages, and publishes them for use by the Brain module.

## Interface 💬
The Interface directory defines the ROS message types and communication interfaces used for interactions between modules such as Vision, Brain, and Control.

## Installation & Run
Prerequisites
* Ubuntu 22.04
* ROS 2 Humble
* sudo apt-get install ros-humble-backward-ros
* sudo apt install ros-humble-behaviortree-cpp-v3

```bash
mkdir  ~/INHA_Soccer
git clone https://github.com/Inha-united-soccer/INHA_Soccer

# Build 
./scripts/build.sh

# Start
./scripts/start.sh
