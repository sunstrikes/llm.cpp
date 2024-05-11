cmake_minimum_required(VERSION 3.25)

set(CMAKE_OSX_SYSROOT "/Library/Developer/CommandLineTools/SDKs/MacOSX14.4.sdk")
set(CMAKE_CXX_STANDARD 23)
SET(CMAKE_C_FLAGS "-O3 -g -Wno-unused-result -Wno-ignored-pragmas -Wno-unknown-attributes")
SET(CMAKE_CXX_FLAGS "-O3 -g -Wno-unused-result -Wno-ignored-pragmas -Wno-unknown-attributes")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++23 -DEIGEN_NO_DEBUG")

project(llm.cpp)
set(BREW_DIR /opt/homebrew/Cellar)
#eigen3
find_package (Eigen3 3.4 REQUIRED NO_MODULE)
include_directories(${BREW_DIR}/eigen/3.4.0_1/include/eigen3)
#boost
#find_package(Boost 1.76.0 REQUIRED COMPONENTS filesystem)
#include_directories(${Boost_INCLUDE_DIRS})

aux_source_directory(./dev/src DIR_SRCS)

add_executable(train_gpt train_gpt2.c)

add_executable(cpu_train_gpt ${DIR_SRCS})
#add_test (test_2_10 Demo 2 10)

#set_tests_properties (test_2_10
#        PROPERTIES PASS_REGULAR_EXPRESSION "is 1024")