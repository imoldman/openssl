set_property(GLOBAL PROPERTY USE_FOLDERS On)

project(openssl CXX)
cmake_minimum_required(VERSION 2.6)
set (CMAKE_BACKWARDS_COMPATIBILITY 2.6)
file(GLOB_RECURSE src RELATIVE ${CMAKE_CURRENT_SOURCE_DIR}
    "*.h"
    "*.c"
    )

if (${BUILD_SHARED_LIBS})
    add_custom_target(openssl
        COMMAND cd "${CMAKE_CURRENT_SOURCE_DIR}"
        COMMAND nmake OnlyDll -f "${CMAKE_CURRENT_SOURCE_DIR}/ms/ntdll.mak"
        SOURCES ${src}
        )
else()
    add_custom_target(openssl
        COMMAND cd "${CMAKE_CURRENT_SOURCE_DIR}"
        COMMAND nmake OnlyLib -f "${CMAKE_CURRENT_SOURCE_DIR}/ms/nt.mak"
        SOURCES ${src}
        )
endif()
