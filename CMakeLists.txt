cmake_minimum_required(VERSION 3.1)

set(PROJ_NAME lua)

project(${PROJ_NAME})

include_directories("${PROJECT_SOURCE_DIR}/lua")

file(GLOB HEADERS "${PROJECT_SOURCE_DIR}/lua/onelua.c")

source_group("Headers" FILES ${HEADERS})
source_group("Sources" FILES ${SOURCES})

option(BUILD_LUAC "BUILD LUAC" off)

if(${BUILD_LUAC})
    add_definitions(-DMAKE_LUAC)
else()
    add_definitions(-DMAKE_LUA)
endif()

add_executable(
    ${PROJ_NAME}
    ${SOURCES}
    ${HEADERS}
)

target_link_libraries(
    ${PROJ_NAME}
    m
)
