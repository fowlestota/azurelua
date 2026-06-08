cmake_minimum_required(VERSION 3.16)
project(lua LANGUAGES C)

file(GLOB LUA_SOURCES CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.c")
file(GLOB LUA_HEADERS CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h")

set(LUA_MAIN src/lua.c)
list(REMOVE_ITEM LUA_SOURCES ${LUA_MAIN})

add_library(azurelua SHARED ${LUA_SOURCES} ${LUA_HEADERS})
target_compile_features(azurelua PRIVATE c_std_99)