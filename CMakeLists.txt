cmake_minimum_required(VERSION 2.8.12)
project(gason)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -fno-rtti -fno-exceptions")
if(CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -stdlib=libc++")
endif()

add_compile_options(-Wall -Wextra -O2)

add_library(gason STATIC src/gason.cpp)
link_libraries(gason)

add_library(gasonmem STATIC src/gason.cpp src/memorystat.cpp)
link_libraries(gasonmem)

add_executable(test-suite src/test-suite.cpp)
add_executable(gasonpp src/pretty-print.cpp)

