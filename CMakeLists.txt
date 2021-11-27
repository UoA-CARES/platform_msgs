cmake_minimum_required(VERSION 2.8.3)
project(platform_msgs)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)

## Find catkin macros and libraries
## if COMPONENTS list like find_package(catkin REQUIRED COMPONENTS xyz)
## is used, also find other catkin packages
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  message_generation
  geometry_msgs
  sensor_msgs
  actionlib_msgs
)

## In order to add messages, adding .msg files in msg/ is enough.
## Don't need to modify following code..
file(GLOB msg_files "msg/*.msg")
foreach (file ${msg_files})
    get_filename_component(file_short ${file} NAME)
    list(APPEND msg_base_files ${file_short})
endforeach ()

add_message_files(DIRECTORY msg FILES ${msg_base_files})
message(STATUS "+++ Messages: ${msg_base_files}")

## In order to add services, adding .srv files in srv/ is enough
## Don't need to modify following code.
file(GLOB srv_files "srv/*.srv")
foreach (file ${srv_files})
    get_filename_component(file_short ${file} NAME)
    list(APPEND srv_base_files ${file_short})
endforeach ()

add_service_files(DIRECTORY srv FILES ${srv_base_files})
message(STATUS "+++ Services: ${srv_base_files}")

## In order to add actions, adding .action files in action/ is enough
## Don't need to modify following code.
file(GLOB action_files "action/*.action")
foreach (file ${action_files})
    get_filename_component(file_short ${file} NAME)
    list(APPEND action_base_files ${file_short})
endforeach ()

add_action_files(DIRECTORY action FILES ${action_base_files})
message(STATUS "+++ Actions: ${action_base_files}")

generate_messages(
    DEPENDENCIES
    std_msgs
    geometry_msgs
    sensor_msgs
    actionlib_msgs 
)

catkin_package(
    CATKIN_DEPENDS message_runtime sensor_msgs
)