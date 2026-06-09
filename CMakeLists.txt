cmake_minimum_required(VERSION 3.16)
project(azurelua LANGUAGES C)

file(GLOB LUA_SOURCES CONFIGURE_DEPENDS
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.c"
)

file(GLOB LUA_HEADERS CONFIGURE_DEPENDS
    "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h"
)

set(LUA_MAIN "${CMAKE_CURRENT_SOURCE_DIR}/src/lua.c")
list(REMOVE_ITEM LUA_SOURCES "${LUA_MAIN}")

add_library(azurelua_shared SHARED
    ${LUA_SOURCES}
    ${LUA_HEADERS}
)

target_compile_features(azurelua_shared PRIVATE c_std_99)

target_include_directories(azurelua_shared PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>
)

set_target_properties(azurelua_shared PROPERTIES
    OUTPUT_NAME lua
)

add_library(azurelua_static STATIC
${LUA_SOURCES}
${LUA_HEADERS}
)

target_compile_features(azurelua_static PRIVATE c_std_99)

target_include_directories(azurelua_static PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>
)

set_target_properties(azurelua_static PROPERTIES
    OUTPUT_NAME lua
)