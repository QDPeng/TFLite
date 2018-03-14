project(TFLITE)
cmake_minimum_required(VERSION 3.4.1)
add_definitions(-std=c++11)

#file(GLOB_RECURSE tf_lite_src *.*)
# file(GLOB_RECURSE tf_lite_include *.h)
# INCLUDE_DIRECTORIES(${tf_lite_include})

set(OBJ_TRACK ${CMAKE_CURRENT_SOURCE_DIR}/object_tracking)
aux_source_directory(${OBJ_TRACK} track_src)
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR} image_src)

add_library(tflite SHARED ${image_src} ${track_src})
include_directories(${image_src} ${track_src})
target_link_libraries(tflite
                      android
                      log
                      jnigraphics
                      m
                      atomic
                      z)
