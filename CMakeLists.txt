cmake_minimum_required(VERSION 3.9)
project(path_planner)                    
set(CMAKE_CXX_STANDARD 20)              

find_package(ompl REQUIRED)


include_directories(src/planner/)
include_directories(/usr/include/eigen3/)
#include_directories(/usr/local/include/ompl-1.6/) 
include_directories(/opt/ros/humble/include/ompl-1.6/)
#include_directories(/usr/include/fcl)

add_library(3dPathPlanner SHARED src/planner/planner.cpp )

set( HEADER 
	src/planner/planner.h
)

set( SRC
	src/planner/planner.cpp	
)

install(TARGETS 3dPathPlanner DESTINATION /usr/lib)
install(FILES ${HEADER} DESTINATION /usr/include/3dPathPlanner)
