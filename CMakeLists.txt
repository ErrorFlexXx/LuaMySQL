cmake_minimum_required(VERSION 3.9)

project(LuaMySQL)

file(GLOB SRC
    src/*.cpp
    src/*.h
)

add_library(${PROJECT_NAME} STATIC ${SRC})
target_link_libraries(${PROJECT_NAME} luajit mariadbclient)

target_include_directories(${PROJECT_NAME}
    PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src>
    $<INSTALL_INTERFACE:include/${PROJECT_NAME}>  # <prefix>/include/${PROJECT_NAME}
    PRIVATE
    src
)

if(MSVC)
	target_compile_options(${PROJECT_NAME} PRIVATE /W3 /D_CRT_SECURE_NO_WARNINGS)
else()
	target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wno-implicit-fallthrough)
endif()
