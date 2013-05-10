set_property(GLOBAL PROPERTY USE_FOLDERS On)

project(openssl CXX)
cmake_minimum_required(VERSION 2.6)
set (CMAKE_BACKWARDS_COMPATIBILITY 2.6)
file(GLOB_RECURSE src RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}
    "openssl-0.9.8r/*.h"
    "openssl-0.9.8r/*.c"
    )

add_custom_target(openssl
                  COMMAND "${CMAKE_CURRENT_SOURCE_DIR}/build_modified_lib.bat"
                  SOURCES ${src}
                  )