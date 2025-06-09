cmake_minimum_required(VERSION 3.15)

project(stb LANGUAGES CXX)

option(STB_VORBIS "Enable stb vorbis" ON)

add_library(stb INTERFACE)
add_library(stb::stb ALIAS stb)

target_include_directories(stb INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

install(
	DIRECTORY
		${CMAKE_CURRENT_SOURCE_DIR}
	DESTINATION
		${CMAKE_CURRENT_SOURCE_DIR}
)

if(STB_VORBIS)
    add_library(stb_vorbis "${CMAKE_CURRENT_SOURCE_DIR}/stb_vorbis.c")
    add_library(stb::vorbis ALIAS stb_vorbis)
endif()

