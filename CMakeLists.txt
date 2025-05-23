# ArduinoJson - https://arduinojson.org
# Copyright © 2014-2025, Benoit BLANCHON
# MIT License

cmake_minimum_required(VERSION 3.15)

idf_component_register(SRCS ""
                      INCLUDE_DIRS "src"
                      REQUIRES arduino-esp32
                      )

project(ArduinoJson VERSION 7.4.1)

if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME)
	include(CTest)
endif()

add_subdirectory(src)

if(CMAKE_PROJECT_NAME STREQUAL PROJECT_NAME AND BUILD_TESTING)
	include(extras/CompileOptions.cmake)
	add_subdirectory(extras/tests)
	add_subdirectory(extras/fuzzing)
endif()
