cmake_minimum_required (VERSION 3.14)
set(CMAKE_HOST_SYSTEM, Windows)
project (CMakeHelloWorld)

#version number
set (CMakeHelloWorld_VERSION_MAJOR 1)
set (CMakeHelloWorld_VERSION_MINOR 0)

#include the subdirectory containing our libs
# add_subdirectory (Hello)
# include_directories(Hello)

#indicate the entry point for the executable
add_executable (CMakeHelloWorld  main.cpp)

# Indicate which libraries to include during the link process.
# target_link_libraries (CMakeHelloWorld Hello)

# install (TARGETS CMakeHelloWorld DESTINATION bin)