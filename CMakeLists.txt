cmake_minimum_required(VERSION 3.6)
project(DXSDK DESCRIPTION "DirectX Toolkit")

add_library(dxsdk INTERFACE)
# target_inlude_directories(dxsdk Include)

target_inlude_directories(dxsdk
    INTERFACE
    $<BUILD_INTERFACE:"${CMAKE_SOURCE_DIR}/Include">
    $<INSTALL_INTERFACE:include/dxsdk>
)

install(TARGETS dxsdk
    EXPORT dxsdk_interface
)

file(GLOB dxsdk_files ${CMAKE_SOURCE_DIR}/Include/*.h)
install(FILES ${dxsdk_files} DESTINATION include/dxsdk)

install(EXPORT dxsdk_interface DESTINATION lib/dxsdk FILE dxsdk-config.cmake)