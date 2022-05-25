cmake_minimum_required(VERSION 2.8.3)

project(marvel_v1)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  std_msgs
  visualization_msgs
  roslaunch
)

catkin_package(LIBRARIES CATKIN_DEPENDS std_msgs roscpp geometry_msgs visualization_msgs)

include_directories(${catkin_INCLUDE_DIRS})

#add_executable(serving_publisher src/serving_publisher.cpp)
#add_dependencies(serving_publisher ${${PROJECT_NAME}_EXPORTED_TARGETS} ${catkin_EXPORTED_TARGETS})
#target_link_libraries(serving_publisher ${catkin_LIBRARIES})

foreach(dir config launch meshes urdf)
	install(DIRECTORY ${dir}/
		DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach(dir)
