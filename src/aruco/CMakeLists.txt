cmake_minimum_required(VERSION 2.8.3)
project(aruco)

## Start Global Marker

## End Global Marker

## Check C++11 / C++0x
include(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++0x" COMPILER_SUPPORTS_CXX0X)
if(COMPILER_SUPPORTS_CXX11)
    set(CMAKE_CXX_FLAGS "-std=c++11")
elseif(COMPILER_SUPPORTS_CXX0X)
    set(CMAKE_CXX_FLAGS "-std=c++0x")
else()
    message(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support. Please use a different C++ compiler.")
endif()

include_directories(
  /usr/include/opencv2
  ${OpenCV_INCLUDE_DIRS}
)

include_directories(include)

add_library(aruco
	    src/aruco/ar_omp.cpp
	    src/aruco/arucofidmarkers.cpp
 	    src/aruco/board.cpp
	    src/aruco/boarddetector.cpp
	    src/aruco/cameraparameters.cpp
	    src/aruco/chromaticmask.cpp
	    src/aruco/cvdrawingutils.cpp
	    src/aruco/highlyreliablemarkers.cpp
	    src/aruco/marker.cpp
	    src/aruco/markerdetector.cpp
	    src/aruco/subpixelcorner.cpp
           )
target_link_libraries(aruco
                      opencv_core 
                      opencv_imgproc 
                      opencv_highgui 
                      opencv_contrib
                      opencv_legacy
                      opencv_photo
                      opencv_video
                      opencv_videostab
		      opencv_calib3d
		      opencv_ml
                      )


