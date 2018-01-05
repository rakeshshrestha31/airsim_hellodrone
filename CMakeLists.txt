cmake_minimum_required(VERSION 3.5.0)
project(HelloDrone)

set(AIRSIM_ROOT $ENV{AIRSIM_PATH})

LIST(APPEND CMAKE_MODULE_PATH ${AIRSIM_ROOT}/cmake/cmake-modules ${AIRSIM_ROOT}/external/rpclib/cmake)
INCLUDE("${AIRSIM_ROOT}/cmake/cmake-modules/CommonSetup.cmake")
INCLUDE(${AIRSIM_ROOT}/external/rpclib/cmake/Findrpclib.cmake)
CommonSetup()

IncludeEigen()

SetupConsoleBuild()

message(STATUS "${RPCLIB_INCLUDE_DIR}")

## Specify additional locations of header files
include_directories(
        ${AIRSIM_ROOT}/HelloDrone
        ${AIRSIM_ROOT}/AirLib/include
        ${RPCLIB_INCLUDE_DIR}
        ${AIRSIM_ROOT}/MavLinkCom/include
        ${AIRSIM_ROOT}/MavLinkCom/common_utils)

add_executable(HelloDrone main.cpp)
target_link_libraries(HelloDrone
        ${AIRSIM_ROOT}/build_debug/output/lib/libAirLib.a
        ${AIRSIM_ROOT}/build_debug/output/lib/libAirSim-rpclib.a)

