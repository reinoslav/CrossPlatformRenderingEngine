cmake_minimum_required(VERSION 3.13)
project(CrossPlatformRenderingEngine)

set(CMAKE_CXX_STANDARD 17)

set(SOURCE_FILES main.cpp)
add_executable(cross_rendering ${SOURCE_FILES})

find_package(OpenGL REQUIRED COMPONENTS OpenGL)
find_package(GLUT REQUIRED)

if(NOT ${OPENGL_FOUND})
    message("OPENGL not found")
endif()

add_dependencies(cross_rendering OpenGL::OpenGL)
include_directories(${GLUT_INCLUDE_DIRS})

target_link_libraries(cross_rendering OpenGL::OpenGL ${GLUT_LIBRARY})
