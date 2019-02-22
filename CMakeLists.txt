cmake_minimum_required(VERSION 3.13)
project(safe_number)

set(CMAKE_CXX_STANDARD 11)

include_directories(include)

add_executable(safe_number_demo main.cpp src/safenumber/safenumber.cpp)