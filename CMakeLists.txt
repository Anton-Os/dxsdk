cmake_minimum_required(VERSION 3.6)
project(DXSDK DESCRIPTION "DirectX Toolkit")

add_library(dxsdk INTERFACE)
# target_inlude_directories(dxsdk Include)

target_include_directories(dxsdk
    INTERFACE
    $<BUILD_INTERFACE:"${CMAKE_SOURCE_DIR}/Include">
    $<INSTALL_INTERFACE:include/dxsdk>
)

install(TARGETS dxsdk
    EXPORT dxsdk_interface
)

file(GLOB dxsdk_headers ${CMAKE_SOURCE_DIR}/Include/*.h)
file(GLOB dxsdk_inl ${CMAKE_SOURCE_DIR}/Include/*.inl)

install(FILES ${dxsdk_headers} ${dxsdk_inl} DESTINATION include/dxsdk)

install(EXPORT dxsdk_interface DESTINATION lib/dxsdk FILE dxsdk-config.cmake)