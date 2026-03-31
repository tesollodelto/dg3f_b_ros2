cmake_minimum_required(VERSION 3.8)
project(dg3f_b_driver)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(trajectory_msgs REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(delto_hardware REQUIRED)

install(
  DIRECTORY config urdf launch
  DESTINATION share/${PROJECT_NAME}
)

### test control DG3F example
add_executable(dg3f_b_test_cpp src/dg3f_b_test.cpp)
ament_target_dependencies(dg3f_b_test_cpp rclcpp trajectory_msgs)

install(
  PROGRAMS
  script/dg3f_b_jtc_test.py
  DESTINATION lib/${PROJECT_NAME}
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
