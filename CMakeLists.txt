cmake_minimum_required(VERSION 3.5)
project(opencv_robot)

# 查找 OpenCV
find_package(OpenCV REQUIRED)

# 查找 ROS 2 依赖
find_package(rclcpp REQUIRED)

# 创建可执行文件
add_executable(camera_feed src/dart.cpp)  # 确保源文件路径正确

# 为目标添加 ROS 2 和 OpenCV 依赖
ament_target_dependencies(camera_feed
  rclcpp
  OpenCV
)

# 安装目标
install(TARGETS
  camera_feed
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()
