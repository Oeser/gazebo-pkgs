cmake_minimum_required(VERSION 2.8.3)
project(gazebo_grasp_plugin)

add_definitions(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
#find_package(catkin REQUIRED COMPONENTS
#  gazebo_ros
#  geometry_msgs
#  roscpp
#  std_msgs
#)

find_package(gazebo REQUIRED)

## Uncomment this if the package has a setup.py. This macro ensures
## modules and global scripts declared therein get installed
## See http://ros.org/doc/api/catkin/html/user_guide/setup_dot_py.html
# catkin_python_setup()

###################################
## catkin specific configuration ##
###################################
## The catkin_package macro generates cmake config files for your package
## Declare things to be passed to dependent projects
## INCLUDE_DIRS: uncomment this if you package contains header files
## LIBRARIES: libraries you create in this project that dependent projects also need
## CATKIN_DEPENDS: catkin_packages dependent projects also need
## DEPENDS: system dependencies of this project that dependent projects also need
#catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES gazebo_grasp_fix
#  CATKIN_DEPENDS gazebo_ros geometry_msgs roscpp std_msgs
#  DEPENDS gazebo 
#)

###########
## Build ##
###########

## Specify additional locations of header files
## Your package locations should be listed before other locations
# include_directories(include)
include_directories(
  include
  ${GAZEBO_INCLUDE_DIRS}
)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

## Declare a cpp library
add_library(gazebo_grasp_fix SHARED src/GazeboGraspFix.cpp src/GazeboGraspGripper.cpp)

## Add cmake target dependencies of the executable/library
## as an example, message headers may need to be generated before nodes
# add_dependencies(gazebo_grasp_plugin_node gazebo_grasp_plugin_generate_messages_cpp)
#add_dependencies(gazebo_grasp_fix ${catkin_EXPORTED_TARGETS})

## Specify libraries to link a library or executable target against

target_link_libraries(gazebo_grasp_fix 
	${GAZEBO_LIBRARIES} 
	${Boost_LIBRARIES}
)
