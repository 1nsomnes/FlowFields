cmake_minimum_required(VERSION 3.28)
project(FlowFields)

set(CMAKE_CXX_STANDARD 20)

# Define the path to the GLFW headers and libraries
set(GLFW_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/src/Dependencies/GLFW)
set(GLFW_LIB_DIR ${CMAKE_SOURCE_DIR}/src/Dependencies/GLFW/lib)

# Add the GLFW header files
include_directories(${GLFW_INCLUDE_DIR})

# Add the GLFW libraries
find_library(GLFW_LIB glfw3 PATHS ${GLFW_LIB_DIR})

# Add the executable
add_executable(FlowFields src/main.cpp)

# Link the GLFW library
target_link_libraries(FlowFields ${GLFW_LIB})

# Link against macOS frameworks and OpenGL
target_link_libraries(FlowFields "-framework Cocoa")
target_link_libraries(FlowFields "-framework IOKit")
target_link_libraries(FlowFields "-framework CoreFoundation")
target_link_libraries(FlowFields "-framework CoreVideo")
target_link_libraries(FlowFields "-framework OpenGL")
