cmake_minimum_required(VERSION 3.1)

option(HUNTER_ENABLED "Enable Hunter package manager" OFF)
include(${CMAKE_CURRENT_LIST_DIR}/shared/cmake/HunterGate.cmake)

HunterGate(
  URL "https://github.com/ruslo/hunter/archive/v0.22.35.tar.gz"
  SHA1 "3876b753b8c0dcb7d62758c9d5ef673d2c0d0ff7"
)

include(${CMAKE_CURRENT_LIST_DIR}/optional/CMakeLists.txt)
