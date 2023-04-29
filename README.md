#Tetris

This project used learning cmake and conan

##Current build commands for my system:

conan install . --output-folder=build --build=missing
cmake --preset conan-default
cd build
cmake .. -G "Visual Studio 17 2022" -DCMAKE_TOOLCHAIN_FILE=conan_toolchain.cmake
cmake --build . --config Release
