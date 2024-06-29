# Set the minimum version of CMake required
cmake_minimum_required(VERSION 3.10)

# Define the project and specify the languages used
project(GameProject VERSION 1.0 LANGUAGES CXX)

# Specify the C++ standard
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# Use pkg-config to find and setup SDL2, SDL2_image, and SDL2_mixer
find_package(PkgConfig REQUIRED)
pkg_search_module(SDL2 REQUIRED sdl2)
pkg_search_module(SDL2_MIXER REQUIRED SDL2_mixer)

# Include directories for header files
include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_MIXER_INCLUDE_DIRS})

# Define the source file(s)
set(SOURCE_FILES game.cpp)

# Define the executable that will be built from the source file(s)
add_executable(Game ${SOURCE_FILES})

# Specify the libraries to link against
target_link_libraries(Game ${SDL2_LIBRARIES} ${SDL2_MIXER_LIBRARIES} SDL2_image pthread)