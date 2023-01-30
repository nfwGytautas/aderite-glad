cmake_minimum_required(VERSION 3.22)
project(glad)

set(CMAKE_CXX_STANDARD 17)

# Files
file(GLOB_RECURSE DEBUG_FILES ${CMAKE_CURRENT_SOURCE_DIR}/debug/src/*.c ${CMAKE_CURRENT_SOURCE_DIR}/debug/include/*.h)
file(GLOB_RECURSE RELEASE_FILES ${CMAKE_CURRENT_SOURCE_DIR}/release/src/*.c ${CMAKE_CURRENT_SOURCE_DIR}/release/include/*.h)

# PIC
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

# Output directory
set(CMAKE_BINARY_DIR ${PROJECT_SOURCE_DIR}/build/)

# Debug lib
add_library(glad_debug ${DEBUG_FILES})
target_include_directories(glad_debug PUBLIC debug/include/)

# Release lib
add_library(glad ${RELEASE_FILES})
target_include_directories(glad PUBLIC release/include/)
