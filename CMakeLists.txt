cmake_minimum_required(VERSION 3.8)
project(my_robot_interfaces)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)
find_package(turtlesim REQUIRED)
find_package(rosidl_default_generators REQUIRED)


rosidl_generate_interfaces(${PROJECT_NAME}
"msg/HardwareStatus.msg"
"msg/LedStates.msg"
"msg/SpawnedTurtle.msg"
"srv/GetActiveTurtles.srv"
"srv/ComputeRectangleArea.srv"
"srv/SetLed.srv"
"action/CountUntil.action"
DEPENDENCIES turtlesim
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
