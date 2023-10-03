cmake_minimum_required(VERSION 3.10)

project(my_sample_lib)

add_library(my_sample_lib STATIC my_sample_lib.cpp)

install(TARGETS my_sample_lib
        EXPORT my_sample_lib_targets
        ARCHIVE DESTINATION lib
        LIBRARY DESTINATION lib
        RUNTIME DESTINATION bin)

install(FILES my_sample_lib.h DESTINATION include)


# Generate and install *-targets.cmake 
install(EXPORT my_sample_lib_targets
        FILE my_sample_lib-targets.cmake
        NAMESPACE my_sample_lib::
        DESTINATION share/my_sample_lib/cmake)

# Simple *-config.cmake file without any conditions
file(WRITE "${CMAKE_CURRENT_BINARY_DIR}/my_sample_lib-config.cmake" 
"include(\"\${CMAKE_CURRENT_LIST_DIR}/my_sample_lib-targets.cmake\")")

install(FILES "${CMAKE_CURRENT_BINARY_DIR}/my_sample_lib-config.cmake"
        DESTINATION share/my_sample_lib/cmake)
