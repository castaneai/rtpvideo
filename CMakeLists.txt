cmake_minimum_required(VERSION 2.8)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake")

set(BUILD_LIBRTPVIDEO OFF CACHE BOOL "Build librtpvideo" FORCE)
set(VERSION_MAJOR 0)
set(VERSION_MINOR 1)
set(VERSION_PATCH 0)
set(VERSION_FULL ${VERSION_MAJOR}.${VERSION_MINOR}.${VERSION_PATCH})
add_definitions(-DRTPVIDEO_VERSION_MAJOR=${VERSION_MAJOR}
                -DRTPVIDEO_VERSION_MINOR=${VERSION_MINOR}
                -DRTPVIDEO_VERSION_PATCH=${VERSION_PATCH})
project(rtpvideo)
if(NOT CMAKE_BUILD_TYPE)
    #set(CMAKE_BUILD_TYPE Debug)
endif()

add_subdirectory(testvideosend)
#add_executable(ClangUML src/main.c)
#target_link_libraries(ClangUML LINK_PUBLIC LibClangUML)
add_library(rtpvideo SHARED src/rtpvideotx.c)
target_include_directories(rtpvideo PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include)

