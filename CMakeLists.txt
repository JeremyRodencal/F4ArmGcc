cmake_minimum_required (VERSION 3.14)
project (CMakeHelloWorldProject C CXX ASM)

#version number
set (CMakeHelloWorldProject_VERSION_MAJOR 1)
set (CMakeHelloWorldProject_VERSION_MINOR 0)

# STM32G0 repository path.
set(STM32G0_REPO_PATH STM32CubeG0)

# Interface target for the STM32CubeG0
add_library(STM32CubeG0 INTERFACE)
target_include_directories(STM32CubeG0
    INTERFACE ${STM32G0_REPO_PATH}/Drivers/CMSIS/Device/ST/STM32G0xx/Include
              ${STM32G0_REPO_PATH}/Drivers/STM32G0xx_HAL_Driver/Inc
              ${STM32G0_REPO_PATH}/Drivers/CMSIS/Include
              ${STM32G0_REPO_PATH}/Drivers/CMSIS/DSP/Include
)

# Setup our executable target
add_executable (CMakeHelloWorld main.cpp startup_stm32g0b1retx.s system_stm32g0xx.cpp)
target_compile_definitions(CMakeHelloWorld PUBLIC STM32G0B1xx)
target_link_libraries(CMakeHelloWorld STM32CubeG0)
target_link_options(CMakeHelloWorld PRIVATE "LINKER:-T,../STM32G0B1RETX_FLASH.ld")
