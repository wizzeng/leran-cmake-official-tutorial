# 1. Set the minimum required version of CMake to be 3.10
# The first command at the beginning of the Top-Level `CMakeLists.txt` file.
# LearnMore: `FATAL_ERROR` param is accpetable, indicated that occuring an Error instead a Warning when cmake failed.
# Ignored by CMake 2.6 and higher 
# LearnMore: `max_policy` param is accetable, specifies the MAXIMUM VERSION of Cmake policy.
cmake_minimum_required(VERSION 3.10)

# 2: Create a project named Tutorial
# 7: Set the project version number as 1.0 in the above project command
project(Tutorial VERSION 1.0)

# Learn more: `cmake_minimum_require` directive will set this variable.
message(
  "Cmake's minimum version is ${CMAKE_MINIMUM_REQUIRED_VERSION}."
  "Current major version is ${CMAKE_MAJOR_VERSION}, "
  "minor version is ${CMAKE_MINOR_VERSION}"
)

# 6: Set the variable CMAKE_CXX_STANDARD to 11
# and the variable CMAKE_CXX_STANDARD_REQUIRED to True
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED)

# 8: Use configure_file to configure and copy TutorialConfig.h.in to
# TutorialConfig.h
configure_file(TutorialConfig.h.in TutorialConfig.h)

# 3: Add an executable called Tutorial to the project
# Hint: Be sure to specify the source file as tutorial.cxx
add_executable(Tutorial tutorial.cxx)

# 9: Use target_include_directories to include ${PROJECT_BINARY_DIR}
target_include_directories(Tutorial PUBLIC "${PROJECT_BINARY_DIR}")