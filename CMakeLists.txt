cmake_minimum_required (VERSION 3.23)

project ("Tetris")

set(SOURCES
    source/Tetris.cpp
)

find_package(SFML 2.5.1 COMPONENTS system window graphics audio REQUIRED)
include_directories(${SFML_INCLUDE_DIRS})

add_executable (${PROJECT_NAME}
    ${SOURCES}
)
target_link_libraries(${PROJECT_NAME}
    ${SFML_LIBRARIES}
)

set_target_properties(${PROJECT_NAME} PROPERTIES
    RUNTIME_OUTPUT_DIRECTORY_RELEASE ${CMAKE_BINARY_DIR}/bin/Release
    RUNTIME_OUTPUT_DIRECTORY_DEBUG ${CMAKE_BINARY_DIR}/bin/Debug
)

set(OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    get_target_property(OUTPUT_DIRECTORY ${PROJECT_NAME} RUNTIME_OUTPUT_DIRECTORY_DEBUG)
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
    get_target_property(OUTPUT_DIRECTORY ${PROJECT_NAME} RUNTIME_OUTPUT_DIRECTORY_RELEASE)
endif()

add_custom_command(TARGET ${PROJECT_NAME} POST_BUILD 
    COMMAND ${CMAKE_COMMAND} -E copy_directory 
        ${CMAKE_SOURCE_DIR}/images
        ${OUTPUT_DIRECTORY}/images
)
