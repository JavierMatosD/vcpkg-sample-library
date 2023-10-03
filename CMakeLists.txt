cmake_minimum_required(VERSION 3.10)

project(my_sample_lib)

add_library(my_sample_lib STATIC my_sample_lib.cpp)

install(TARGETS my_sample_lib
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib
        RUNTIME DESTINATION bin)

install(FILES my_sample_lib.h DESTINATION include)

