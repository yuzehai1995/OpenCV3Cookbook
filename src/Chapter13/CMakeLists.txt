# cmake for OpenCV Cookbook 3rd edition chapter 13
# your opencv/build directory should be in your system PATH

# set minimum required version for cmake
cmake_minimum_required(VERSION 2.8)

set( CMAKE_CXX_FLAGS "-std=c++11 -O3" )  #加入c++11编译要求

find_package( OpenCV 3.1 REQUIRED )

include_directories( 
    ${OpenCV_INCLUDE_DIRS} 
)

# add executable
add_executable( tracker tracker.cpp)
add_executable( flow flow.cpp)
add_executable( oTracker oTracker.cpp)

# link libraries
target_link_libraries( tracker ${OpenCV_LIBS})
target_link_libraries( flow ${OpenCV_LIBS})
target_link_libraries( oTracker ${OpenCV_LIBS})

# copy required images to every directory with executable
SET (IMAGES ${CMAKE_SOURCE_DIR}/../images/bike.avi)
FILE(COPY ${IMAGES} DESTINATION .)

FILE(COPY ${CMAKE_SOURCE_DIR}/../images/goose/ DESTINATION ./goose/)


