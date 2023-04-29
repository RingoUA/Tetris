cmake_minimum_required (VERSION 3.23)

project ("Tetris")

find_package(SFML 2.5.1 COMPONENTS system window graphics audio REQUIRED)


add_executable (${PROJECT_NAME} src/Tetris.cpp)

target_link_libraries(
    ${PROJECT_NAME}
    sfml::sfml sfml-window sfml-graphics)