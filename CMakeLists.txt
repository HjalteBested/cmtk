# Minimum required CMake version
cmake_minimum_required(VERSION 3.12)

# Select Compiler
set(CMAKE_C_COMPILER "clang")
set(CMAKE_CXX_COMPILER "clang++")

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)

# Project name
project(MyProject)

# Add your source files here
set(SOURCES
    src/main.cpp
    src/InterfaceGPT.cpp
)

# Add your header files here
set(HEADERS
    src/Chords.h
    src/InterfaceGPT.h
    libraries/SimpleJSON/json.hpp
)

# Find required packages
find_package(CURL REQUIRED) # libcurl

# Add executable target
add_executable(MyProject ${SOURCES} ${HEADERS})

# Add include directories
target_include_directories(MyProject PUBLIC include)

# Add link libraries
target_link_libraries(MyProject PRIVATE CURL::libcurl)

