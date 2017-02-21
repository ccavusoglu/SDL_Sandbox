set(CMAKE_VERBOSE_MAKEFILE ON)
cmake_minimum_required(VERSION 3.6)
project(SDL_Sandbox)

set(CMAKE_CXX_STANDARD 11)

# Put the FindSDL2.cmake in a folder and tell CMake to find it there
set(CMAKE_MODULE_PATH "C:/Development/CMake/modules")

# This path is used by FindSDL2 module. It will find include and lib folders under this directory.
# This is because find command doesn't include any path for Windows.
# So it won't find anything using default paths.
set(SDL2_PATH "C:/Development/Library")

# CMake parses module files by their names. It will use FindSDL2 in this case.
find_package(SDL2 REQUIRED)

# Explicitly specify paths for SDL_gpu. It's hardcoded and ugly.
set(SDL2_GPU_LIBRARY_PATH "C:/Development/Library/lib/libSDL2_gpu.dll.a")
set(SDL2_GPU_INCLUDE_PATH "C:/Development/Library/include/SDL2_gpu")

# This variable set by the FindSDL2 module.
include_directories(${SDL2_INCLUDE_DIR} ${SDL2_GPU_INCLUDE_PATH})

set(SOURCE_FILES src/main.cpp)
add_executable(SDL_Sandbox ${SOURCE_FILES})

# SDL2MAIN_LIBRARY is also specified within SDL2_LIBRARY by the FindSDL2 module.
# It's needed for Windows specific main function.
message(${SDL2_LIBRARY})

target_link_libraries(SDL_Sandbox
        ${SDL2_LIBRARY}
        ${SDL2_GPU_LIBRARY_PATH})