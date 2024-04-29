cmake_minimum_required(VERSION 3.15)

set(MSVC_NAME "")
if(MSVC_TOOLSET_VERSION MATCHES "140")
    set(MSVC_NAME "VS2015")
elseif(MSVC_TOOLSET_VERSION MATCHES "141")
    set(MSVC_NAME "VS2017")
elseif(MSVC_TOOLSET_VERSION MATCHES "142")
    set(MSVC_NAME "VS2019")
elseif(MSVC_TOOLSET_VERSION MATCHES "143")
    set(MSVC_NAME "VS2022")
else()
    message(FATAL_ERROR "dosent support msvc ${MSVC} compiler")
endif()

set(ARCHITECTURE ${CMAKE_GENERATOR_PLATFORM})

message(STATUS "build with ${MSVC_NAME}/${ARCHITECTURE} compiler....")

set(ASSIMP_INSTALL_DIR ${CMAKE_SOURCE_DIR}/installed/${MSVC_NAME}/${ARCHITECTURE})

message(STATUS "install dir : ${ASSIMP_INSTALL_DIR}")


add_subdirectory(assimp-external)

file(DOWNLOAD "https://raw.githubusercontent.com/xarchx80/Graphics-fundamentals/main/CMake/Example/"  ${CMAKE_SOURCE_DIR}/example)
