cmake_minimum_required(VERSION 3.2)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/shared/cmake)

option(HUNTER_ENABLED "Enable Hunter package manager" OFF)
include(HunterGate)

HunterGate(
  URL "https://github.com/ruslo/hunter/archive/v0.22.36.tar.gz"
  SHA1 "66b28c3e88dd81833851181149df1075c62e8790"
)

project(libigl CXX)

include(${CMAKE_CURRENT_LIST_DIR}/optional/CMakeLists.txt)
