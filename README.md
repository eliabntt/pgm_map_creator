# pgm_map_creator
Create pgm map from Gazebo world file for ROS localization

## Environment
Tested on Ubuntu 20.04, ROS Noetic, Boost 1.71

## Usage

### Add the package to your workspace
0. Create a catkin workspace
1. Clone the package to the src folder
2. `catkin build pgm_map_creator` and source `devel/setup.bash`

### Add the map and insert the plugin
1. Add this line at the end of the world file, before `</world>` tag:
`<plugin filename="libcollision_map_creator.so" name="collision_map_creator"/>`

### Create the pgm map file
1a. Open a terminal, run gzerver with the map file
`gzserver src/pgm_map_creator/world/<map file>`
1b. Launch the world file normally
2. Open another terminal, launch the request_publisher node
`roslaunch pgm_map_creator request_publisher.launch`
3. Wait for the plugin to generate map. It will be located in the map folder

## Map Properties
Currently, please update the argument value in launch/request_publisher.launch file.

## Edits
You can edit the map in an external software like [GIMP](https://www.gimp.org/). 

## Todo
- generation of the YAML file
- options through command line
