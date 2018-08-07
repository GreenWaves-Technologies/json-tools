cmake_minimum_required(VERSION 3.5)
project(json-tools VERSION 1.0.0)
set (CMAKE_CXX_STANDARD 11)

add_library(json STATIC
    src/jsmn.cpp
    src/json.cpp
)
target_include_directories(json PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/include)

set_target_properties(bar_hidden PROPERTIES
	VERSION ${PROJECT_VERSION}
	POSITION_INDEPENDENT_CODE ON	# Compile this object code position independent.
)

set(JSON_TOOLS_PYTHON_DIR ${CMAKE_CURRENT_SOURCE_DIR}/python/)
set(JSON_TOOLS_PY_FILES 
    ${JSON_TOOLS_PYTHON_DIR}/json_tools.py)

set(JSON_TOOLS_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include/)
set(JSON_TOOLS_INCLUDE_FILES 
    ${JSON_TOOLS_INCLUDE_DIR}/jsmn.h
    ${JSON_TOOLS_INCLUDE_DIR}/json.hpp
)

install(PROGRAMS ${JSON_TOOLS_PY_FILES} DESTINATION python)
install(FILES ${JSON_TOOLS_INCLUDE_FILES} DESTINATION include)
install(TARGETS json DESTINATION lib)
