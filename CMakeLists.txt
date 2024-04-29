cmake_minimum_required(VERSION 3.15)

set(MSVC_NAME "")
if(MSVC_TOOLSET_VERSION MATCHES "140")
    set(MSVC_NAME "msvc2015")
elseif(MSVC_TOOLSET_VERSION MATCHES "141")
    set(MSVC_NAME "msvc2017")
elseif(MSVC_TOOLSET_VERSION MATCHES "142")
    set(MSVC_NAME "msvc2019")
elseif(MSVC_TOOLSET_VERSION MATCHES "143")
    set(MSVC_NAME "msvc2022")
else()
    message(FATAL_ERROR "dosent support msvc ${MSVC} compiler")
endif()

set(ARCHITECTURE ${CMAKE_VS_PLATFORM_TOOLSET_HOST_ARCHITECTURE})

set(PRE_BUILT_DIR ${CMAKE_SOURCE_DIR}/prebuilt)

set(ASSIMP_INSTALL_DIR ${PRE_BUILT_DIR}/${MSVC_NAME}/${ARCHITECTURE})

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${CMAKE_SOURCE_DIR}/module)

message(STATUS "pre building ... : ${ASSIMP_INSTALL_DIR}")

include(assimp-prebuilt)
include(assimp-build)

