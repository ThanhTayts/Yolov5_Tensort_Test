##################### STANDARD HEADER #########################

cmake_minimum_required(VERSION 3.5)

##################### PROJECT DEF #############################
project(test_yolo)
set(CMAKE_BUILD_TYPE Debug)

include_directories(/usr/local/cuda/include)
link_directories(/usr/local/cuda/lib64)

add_subdirectory(../bytetrack ${CMAKE_CURRENT_BINARY_DIR}/bytetrack)

####################### INCLUDE   #############################

include_directories(${INCLUDE_DIRS} ${GST_INCLUDE_DIRS})
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")
add_executable(${PROJECT_NAME} app_yolov5.cpp)

target_link_libraries(${PROJECT_NAME} PRIVATE detection bytetrack ${OpenCV_LIBS} ${GST_LIBRARIES})