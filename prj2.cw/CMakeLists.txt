cmake_minimum_required(VERSION 3.20)
project(lungs)
set(CMAKE_CXX_STANDARD 20)

option(LIBIGL_USE_STATIC_LIBRARY "Use LibIGL as static library" ON)
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
include(libigl)

igl_include(glfw)
igl_include(opengl)

target_compile_definitions(glfw PUBLIC IGL_VIEWER_VIEWER_QUIET)

find_package(tinysplinecxx CONFIG REQUIRED)

find_package(OpenCV CONFIG REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})

add_subdirectory(src)
