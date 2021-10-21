project(subLib CXX)

add_library(sublib sub_test.cpp)

install(TARGETS sublib)