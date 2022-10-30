set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
#default save directory of .a (static)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
#default save directory of .so  (shared)
#set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
#default save directory of .a and .so ,if not define CMAKE_ARCHVIE_OUTPUT_DIRECTORY 

#CMAKE_RUNTIME_OUTPUT_DIRECTORY save executable software

include_directories(${CMAKE_SOURCE_DIR}/include)
#import include ==> test.h
add_library(test_static STATIC test.cpp)
set_target_properties(test_static PROPERTIES OUTPUT_NAME "test")
set_target_properties(test_static PROPERTIES CLEAN_DIRECT_OUTPUT 1)

add_library(test_shared SHARED test.cpp)
set_target_properties(test_shared PROPERTIES OUTPUT_NAME "test")
set_target_properties(test_shared PROPERTIES CLEAN_DIRECT_OUTPUT 1)


#VERSION
set_target_properties(test_shared PROPERTIES VERSION 1.1 SOVERSION 1.2)

add_executable(test main.cpp)

target_link_libraries(test ${CMAKE_SOURCE_DIR}/lib/libtest.so)

#link static libraries
#target_link_libraries(test ${CMAKE_SOURCE_DIR}/lib/libtest.a)
