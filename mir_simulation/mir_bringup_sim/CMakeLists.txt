# cmake_minimum_required(VERSION 2.8.3)
cmake_minimum_required(VERSION 3.8)

project(mir_bringup_sim)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()


# find_package(catkin REQUIRED)
find_package(ament_cmake REQUIRED)

# catkin_package(
#   CATKIN_DEPENDS
#     gazebo_ros
#     mcr_gazebo_worlds
#     mir_arm_cartesian_control
#     mir_default_robot_config
#     mir_hardware_config
#     robot_state_publisher
#     youbot_gazebo_control
# )


# find_package(mcr_gazebo_worlds REQUIRED)
# find_package(mir_arm_cartesian_control REQUIRED)
# find_package(mir_default_robot_config REQUIRED)
# find_package(mir_teleop REQUIRED)
find_package(robot_state_publisher REQUIRED)
find_package(ros_ign_bridge REQUIRED)
# find_package(youbot_gazebo_control REQUIRED)
# find_package(youbot_driver_ros_interface REQUIRED)


# ### TEST
# if(CATKIN_ENABLE_TESTING)
#   find_package(roslaunch REQUIRED)

#   #roslaunch_add_file_check(. robot:=youbot-brsu-1 robot_env:=brsu-c025)
#   roslaunch_add_file_check(robots)
# endif()


set(
  INSTALL_DIRS
    controller
    robots
)



foreach(dir ${INSTALL_DIRS})
  install(DIRECTORY ${dir}
    DESTINATION share/${PROJECT_NAME})
endforeach()



ament_package()


# ### INSTALLS
# install(DIRECTORY robots/
#   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/robots
# )
# install(FILES robot.launch
#   DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
# )
