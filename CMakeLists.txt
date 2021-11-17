
# Project setup:

cmake_minimum_required(VERSION 3.0.0)

project(lbfgsb)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)


# Executable:

add_executable(lbfgsb src/main.cpp)
target_include_directories(lbfgsb PUBLIC include/)


# Dependencies:

find_package (Eigen3 3.3 REQUIRED NO_MODULE)
target_link_libraries(lbfgsb Eigen3::Eigen)

find_package(OpenMP)
if(OPENMP_FOUND)
    set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()


# Building:

target_compile_options(lbfgsb PRIVATE -O3 -Wall)

# For other projects to include. There may be a better way...
set(${PROJECT_NAME}_INCLUDE_DIRS ${PROJECT_SOURCE_DIR}/include)