cmake_minimum_required(VERSION 3.0.2)
project(cloud_practice)

# add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  eigen_conversions
  geometry_msgs
  pcl_conversions
  pcl_msgs
  pcl_ros
  sensor_msgs
  std_msgs
  roscpp 
  rospy
)

find_package(PCL REQUIRED)

include_directories(include ${catkin_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})

link_directories(${PCL_LIBRARY_DIRS})

catkin_package(
  INCLUDE_DIRS include 
  LIBRARIES ${PROJECT_NAME}
  CATKIN_DEPENDS pcl_conversions pcl_ros roscpp rospy sensor_msgs std_msgs geometry_msgs eigen_conversions
)

add_executable(cloud_creatorJ_1 src/cloud_creator.cpp)
target_link_libraries(cloud_creatorJ_1 
${catkin_LIBRARIES} 
${PCL_LIBRARIES}
)

add_executable(cloud_matching src/cloud_matcher.cpp)
target_link_libraries(cloud_matching
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)

add_executable(cloud_loader src/cloud_loader.cpp)
target_link_libraries(cloud_loader
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)

add_executable(cloud_filter src/cloud_filter.cpp)
target_link_libraries(cloud_filter
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)

add_executable(cloud_downsampler src/cloud_downsampler.cpp)
target_link_libraries(cloud_downsampler
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)

add_executable(cloud_planar_segmenter src/cloud_planar_segmenter.cpp)
target_link_libraries(cloud_planar_segmenter
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)

add_executable(cloud_clusterer src/cloud_clusterer.cpp)
target_link_libraries(cloud_clusterer
  ${catkin_LIBRARIES}
  ${PCL_LIBRARIES}
)