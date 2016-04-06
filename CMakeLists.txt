# Top-Level CMakeList.txt

cmake_minimum_required (VERSION 2.6)
project ( FirstLab )

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
#set(SOURCE_FILES skeleton.cpp)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

add_executable( FirstLab skeleton.cpp )

set(SDL_LIBRARY ${PROJECT_SOURCE_DIR}/SDL/lib)
set(SDL_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/SDL/include)
#set(CMAKE_CXX_COMPILER "C:/MinGW/bin/g++")

#include_directories(${SDL_INCLUDE_DIR})
#link_directories(
#        ${PROJECT_SOURCE_DIR}/lib
#        ${PROJECT_SOURCE_DIR}/include
#)

find_package (SDL)

if ( NOT SDL_FOUND )
    message ( FATAL_ERROR "SDL not found!" )
endif ( NOT SDL_FOUND )

if(SDL_FOUND)
    include_directories(
            ${SDL_INCLUDE_DIR}
            ${PROJECT_SOURCE_DIR}/glm
    )
    link_libraries(${SDL_LIBRARY})
    target_link_libraries(FirstLab ${SDL_LIBRARY})
endif(SDL_FOUND)

