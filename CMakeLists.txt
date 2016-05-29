# CMakeLists files in this project can
# refer to the root source directory of the project as ${HELLO_SOURCE_DIR} and
# to the root binary directory of the project as ${HELLO_BINARY_DIR}.
cmake_minimum_required (VERSION 2.8.11)
project (HELLO)

set(CMAKE_CXX_FLAGS "-std=c++11")

# Recurse into the "src" subdirectory. This does not actually
# cause another cmake executable to run. The same process will walk through
# the project's entire directory structure.
add_subdirectory(src)
add_subdirectory(Test)	

add_executable(hello src\hello.cpp)

# src globs the cpp files into a library
# tests mocks/tests

