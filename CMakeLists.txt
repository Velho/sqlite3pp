# CMake configuration for Sqlite3pp by Iwongu.
# Author : Velho 2015
# Implements simple CMake configuration with Sqlite3 find module.
# TODO Add settings for Boost, STATIC | SHARED, Win(?).

cmake_minimum_required(VERSION 3.0)
project(sqlite3pp)

if(UNIX) # C++11 as default for Unix.
    set(CMAKE_CXX_FLAGS "-std=c++11" ${CMAKE_CXX_FLAGS})
endif(UNIX)

set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake" ${CMAKE_MODULE_PATH})

find_package(Sqlite3 REQUIRED)
include_directories(${Sqlite3_INCLUDE_DIR})

# Lists sources.
set(SRC_LIST
    src/sqlite3pp.cpp
    src/sqlite3ppext.cpp)

# Lists headers.
set(HDR_LIST
    src/sqlite3pp.h
    src/sqlite3ppext.h)

add_library(sqlite3pp ${SRC_LIST} ${HDR_LIST})
target_link_libraries(sqlite3pp ${Sqlite3_LIBRARY})
