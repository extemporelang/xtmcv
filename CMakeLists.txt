cmake_minimum_required(VERSION 3.3)
project(xtmcv C CXX)

message("-------------------")
message("NOTES: ")
message("Build opencv-4+ statically (not dynamic).")
message("Make sure you do the INSTALL step!")
message("You should end up with an install directory containing include and x64 dirs.")
message("You'll need to point CV4_DIR to that install directory.")
message("-------------------")


set(CMAKE_C_STANDARD 99)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_POSITION_INDEPENDENT_CODE ON)

set(CV4_DIR "C:/" CACHE PATH "Path to opencv 4 install directory")

if( NOT DEFINED CV4_DIR )
  message( FATAL_ERROR "You must set the CV4_DIR." )
endif()

if ( MSVC )
    set(CMAKE_CXX_FLAGS_RELEASE "/MT")
    set(CMAKE_CXX_FLAGS_DEBUG "/MTd")
    set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS ON)
    #set(WINDOWS_EXPORT_ALL_SYMBOLS ON)
endif()

include_directories(
  "${CV4_DIR}/include"
)

link_directories(
  "${CV4_DIR}/x64/vc15/bin"
  "${CV4_DIR}/x64/vc15/staticlib"
)

file(GLOB CV_LIBS "${CV4_DIR}/x64/vc15/staticlib/*.lib")

link_libraries(${CV_LIBS})

set(Headers 
    "core.h"
    "videoio.h"
    "highgui_xtm.h"
    "imgcodecs.h"
    "video.h"
    "imgproc.h"
)

set(Sources
    "core.cpp"
    "videoio.cpp"
    "highgui.cpp"
    "imgcodecs.cpp"
    "video.cpp"
    "imgproc.cpp"
)

add_library(xtmcv SHARED ${Sources} ${Headers})