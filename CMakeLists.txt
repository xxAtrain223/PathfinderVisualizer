cmake_minimum_required(VERSION 3.0)
project(PathfinderVisualizer)

include(ExternalProject)
find_package(Git REQUIRED)
find_package(SFML 2 REQUIRED system window graphics)
add_subdirectory(Pathfinder)

file(GLOB_RECURSE pathfinder_visualizer src/*.cpp)

add_executable(pathfinder_visualizer ${pathfinder_visualizer})
set_property(TARGET pathfinder_visualizer PROPERTY CXX_STANDARD 14)
target_include_directories(pathfinder_visualizer PUBLIC ${SFML_INCLUDE_DIR})
target_include_directories(pathfinder_visualizer PUBLIC ${Pathfinder_INCLUDE_DIRS})
target_link_libraries(pathfinder_visualizer ${SFML_LIBRARIES})
target_link_libraries(pathfinder_visualizer ${pathfinder})
