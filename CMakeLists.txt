cmake_minimum_required (VERSION 2.6)
project(json-c)

set(libjson_src arraylist.c  debug.c  json_object.c  json_tokener.c  json_util.c  linkhash.c  printbuf.c)

if(CMAKE_SYSTEM_NAME MATCHES Linux)
  add_definitions(-g -std=c99 -O2)
endif()

if(CMAKE_SYSTEM_NAME MATCHES Windows)
  configure_file (
    "${PROJECT_SOURCE_DIR}/config.h.win32"
    "${PROJECT_BINARY_DIR}/config.h"
  )
  configure_file (
    "${PROJECT_SOURCE_DIR}/json_config.h.win32"
    "${PROJECT_BINARY_DIR}/json_config.h"
  )
endif()

include_directories("${CMAKE_CURRENT_BINARY_DIR}" "${PROJECT_SOURCE_DIR}")
add_library(libjson ${libjson_src})
add_subdirectory (tests)

