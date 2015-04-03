cmake_minimum_required(VERSION 3.1)
project(fred)

set(CMAKE_C_COMPILER /usr/local/bin/gcc-4.9)
set(CMAKE_CXX_COMPILER /usr/local/bin/g++-4.9)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")

set(SOURCE_FILES main.cpp)
add_executable(fred ${SOURCE_FILES})

add_subdirectory(external/googletest)
include_directories(${gtest_SOURCE_DIR}/include)
add_executable(fred_unit test.cpp)
target_link_libraries(fred_unit gtest_main)

add_subdirectory(external/benchmark)
include_directories(${benchmark_SOURCE_DIR}/include)
add_executable(fred_benchmark benchmark.cpp)
target_link_libraries(fred_benchmark benchmark)
