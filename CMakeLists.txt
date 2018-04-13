cmake_minimum_required(VERSION 3.3)
project(LuaMySQL)

file(GLOB_RECURSE SRC
    src/*.cpp
    src/*.h
)

add_library(lua_mysql STATIC ${SRC})
