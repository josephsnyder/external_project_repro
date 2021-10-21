project(superbuildTest CXX)
cmake_minimum_required(VERSION 3.19)

include(ExternalProject)

ExternalProject_Add(
  sublib
  SOURCE_DIR ${CMAKE_SOURCE_DIR}/sublib
	CMAKE_ARGS
		-DCMAKE_INSTALL_PREFIX:PATH=${CMAKE_BINARY_DIR}/sublib
)

add_library(superLib test.cpp)
add_dependencies(superLib sublib)
target_include_directories(superLib PUBLIC ${CMAKE_BINARY_DIR}/sublib)