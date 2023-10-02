cmake_minimum_required(VERSION 3.1 FATAL_ERROR)
project(my_project)

# Add C++11 support
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)

# Find PCL
find_package(PCL 1.8 REQUIRED COMPONENTS common io filters segmentation visualization features)

# Find Boost
# find_package(Boost REQUIRED COMPONENTS thread)

# Include directories
include_directories(
    ${PCL_INCLUDE_DIRS}
)

# Add definitions and compile options suggested by PCL
add_definitions(${PCL_DEFINITIONS})
list(APPEND CMAKE_CXX_FLAGS "${PCL_CXX_FLAGS}")

# Your executable file
add_executable(robust-stem-extraction src/robust-stem-extraction.cpp)

# Linking libraries
# target_link_libraries(${PROJECT_NAME}
#     ${PCL_LIBRARIES}
#     ${Boost_LIBRARIES}
# )
target_link_libraries(robust-stem-extraction ${PCL_LIBRARIES} pcl_visualization)
