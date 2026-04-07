cmake_minimum_required(VERSION 3.8)
project(leo_nav_project)

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(nav2_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

include_directories(include)

add_executable(nav_manager src/nav_manager.cpp)
ament_target_dependencies(nav_manager
  rclcpp
  nav2_msgs
  sensor_msgs
  geometry_msgs
)

install(TARGETS
  nav_manager
  DESTINATION lib/${PROJECT_NAME}
)

install(DIRECTORY launch config maps urdf worlds
  DESTINATION share/${PROJECT_NAME}
)

ament_package()