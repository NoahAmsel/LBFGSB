
# Project setup:

cmake_minimum_required(VERSION 3.0.0)

project(lbfgsb)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)




# Project source code:

file(GLOB_RECURSE MAIN_SOURCES "src/*.hh" "src/*.cc" "src/*.h" "src/*.c" "src/*.hpp" "src/*.cpp")




# Executable:

add_executable(lbfgsb ${MAIN_SOURCES})



# Dependencies:

target_include_directories(lbfgsb PRIVATE "ext/eigen")


find_package(OpenMP)
if(OPENMP_FOUND)
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()


# Building:

target_compile_options(lbfgsb PRIVATE -O3 -Wall)


# Make source files available for '<....>' includes:
target_include_directories(lbfgsb PRIVATE "src")


# Additional Linking

#(none)

