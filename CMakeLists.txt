cmake_minimum_required(VERSION 2.6)
project (exocv)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O3 -pthread")
find_package(OpenCV REQUIRED)

include_directories(include)

file(GLOB exocv_SRCS 	
	${PROJECT_SOURCE_DIR}/src/*.cpp
	${PROJECT_SOURCE_DIR}/include/*.h
)

add_executable(exocv ${exocv_SRCS})

if(OpenCV_FOUND)
	include_directories(${OpenCV_INCLUDE_DIR})
	target_link_libraries(exocv ${OpenCV_LIBRARIES})
endif()