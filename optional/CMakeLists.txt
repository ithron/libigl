cmake_minimum_required(VERSION 3.1)

option(HUNTER_ENABLED "Enable Hunter package manager" OFF)
include(${CMAKE_CURRENT_LIST_DIR}/shared/cmake/HunterGate.cmake)

HunterGate(
  URL "https://github.com/ruslo/hunter/archive/v0.22.35.tar.gz"
  SHA1 "3876b753b8c0dcb7d62758c9d5ef673d2c0d0ff7"
)

project(libigl)

set (CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/../shared/cmake")
# These ensure that lib*.a are placed in the directory where `cmake
# ../optional/` was issued.
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

### conditionally compile certain modules depending on libraries found on the system
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/../shared/cmake)
find_package(CGAL QUIET COMPONENTS Core)
find_package(MATLAB QUIET)
find_package(MOSEK)

### libIGL options: choose between header only and compiled static library
option(LIBIGL_USE_STATIC_LIBRARY "Use LibIGL as static library" ON)

### Adding libIGL: choose the path to your local copy libIGL
include(libigl)

