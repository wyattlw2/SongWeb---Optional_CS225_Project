cmake_minimum_required(VERSION 3.22)

project(cs_225_final)

set(CMAKE_CXX_STANDARD 17)

set(CMAKE_BUILD_TYPE Debug)

# Use build flags same as in class
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pedantic -Wall -Werror -Wfatal-errors -Wextra -Wno-unused-parameter -Wno-unused-variable -Wno-unused-function")

# Use debug config same as in class
set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -D_GLIBCXX_DEBUG -O0 -gdwarf-4")

add_executable(main src/main.cpp src/Graph.cpp src/utils.cpp)

find_package(Catch2 3 REQUIRED)
add_executable(test test/test-main.cpp src/Graph.cpp src/utils.cpp)
target_link_libraries(test PRIVATE Catch2::Catch2WithMain)
add_dependencies(test main)