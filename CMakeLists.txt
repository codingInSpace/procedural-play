cmake_minimum_required(VERSION 3.6)
project(lab1)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -g -lGLEW -DGLEW_STATIC -lglfw3 -lGL -lX11 -lXi -lXrandr -lXxf86vm -lXinerama -lXcursor -lrt -lm -pthread")
#set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(PROJECT_INCLUDE_DIR ${CMAKE_SOURCE_DIR}/include)
set(PROJECT_EXEC_DIR ${CMAKE_SOURCE_DIR}/src)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

message(WARNING "All exec files: ${PROJECT_EXEC_DIR}")

file(GLOB_RECURSE PROJECT_RECURSE_FILES ${PROJECT_EXEC_DIR}/*.c)
set(SOURCE_FILES ${PROJECT_RECURSE_FILES})
add_executable(lab1 ${SOURCE_FILES})

find_package(glfw3 3.2 REQUIRED)
find_package(OpenGL REQUIRED)
include_directories(${PROJECT_INCLUDE_DIR} ${OPENGL_INLCUDE_DIRS} ${GLFW_INCLUDE_DIRS})

#target_include_directories(lab1 PUBLIC ${OPENGL_INCLUDE_DIR})
target_link_libraries(lab1 ${OPENGL_gl_LIBRARY} ${GLFW_LIBRARIES} m)

message(WARNING "All include dirs: ${PROJECT_INCLUDE_DIR}")

