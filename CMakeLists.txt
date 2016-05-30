# CMakeLists files in this project can
# refer to the root source directory of the project as ${HELLO_SOURCE_DIR} and
# to the root binary directory of the project as ${HELLO_BINARY_DIR}.
cmake_minimum_required (VERSION 2.8.11)
project (HELLO)

set(CMAKE_CXX_FLAGS "-std=c++11")

# Git related macros and commands:
find_package(Git)

if(GIT_FOUND)
  message(STATUS "Git package was found: '${GIT_EXECUTABLE}'")
  set(PRINT_VERSION_COMMAND ${GIT_EXECUTABLE} describe)
  set(PRINT_FILE_DATE_COMMAND_STR "${GIT_EXECUTABLE} log --pretty=format:'Author: %an <%ae>%nDate: %ad' --date=short -n 1")
else()
  set(PRINT_VERSION_COMMAND ${CMAKE_COMMAND} -E echo unknown version)
  set(PRINT_FILE_DATE_COMMAND_STR "${CMAKE_COMMAND} -E echo")
endif()

# Doxygen related macros and commands:
find_package(Doxygen)

# Recurse into the "src" subdirectory. This does not actually
# cause another cmake executable to run. The same process will walk through
# the project's entire directory structure.
add_subdirectory(src)
add_subdirectory(Test)	

#file(GLOB SOURCES "src/*.cpp")

#add_executable(hello ${SOURCES})

# src globs the cpp files into a library
# tests mocks/tests

