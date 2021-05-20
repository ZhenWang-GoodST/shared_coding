cmake_minimum_required(VERSION 3.0)
 
project(reconstruct)
 
set(CUDA_USE_STATIC_CUDA_RUNTIME ON) #这一句解决 cannot find -lopencv_dep_cudart
set(CMAKE_CXX_STANDARD 11)
# set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR})
 
 
set(OpenCV_DIR "/home/wz/github/opencv/build") # 指定OpenCV安装路径来区分不同的OpenCV版本
find_package(OpenCV 4  REQUIRED)

find_package(PCL  REQUIRED )
include_directories(${PCL_INCLUDE_DIRS})      
# set(OpenCV_LIB_DIR ${OpenCV_INSTALL_PATH}/lib)
# set(OpenCV_LIB_DIR /home/wz/github/opencv/install/lib)
# set(OpenCV_INCLUDE_DIRS /home/wz/github/opencv/install/include/opencv4)
message(STATUS "OpenCV版本: ${OpenCV_VERSION}")
message(STATUS "    头文件目录：${OpenCV_INCLUDE_DIRS}")
message(STATUS "    库文件目录：${OpenCV_LIB_DIR}")
message(STATUS "    库文件列表：${OpenCV_LIBS}")
include_directories(./)
include_directories(${OpenCV_INCLUDE_DIRS})
link_directories(${OpenCV_LIB_DIR})
 
 
ADD_EXECUTABLE(reconstruct main.cpp)
target_link_libraries(reconstruct 
    ${OpenCV_LIBS}
    ${PCL_LIBRARIES})
# target_include_directories(main ${OpenCV_INCLUDE_DIRS})
