set(CMAKE_VERBOSE_MAKEFILE ON)
cmake_minimum_required(VERSION 3.6)
project(SDL_Sandbox)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_MODULE_PATH "C:/Development/CMake/modules")

#set(SDL2_INCLUDE_DIR "C:/Development/Librarys/include/SDL2")
#set(SDL2_LIBRARY_MAIN "C:/Development/Librarys/lib/libSDL2main.a")
#set(SDL2_LIBRARY "C:/Development/Librarys/lib/libSDL2.dll.a")

find_package(SDL2 REQUIRED)
#find_package(SDL2_IMAGE REQUIRED)

include_directories(
        ${SDL2_INCLUDE_DIR}
        #        ${SDL2_IMAGE_INCLUDE_DIR}
)

set(SOURCE_FILES
        src/main.cpp)
add_executable(SDL_Sandbox ${SOURCE_FILES})

set(SDL_GPU_LIBRARY_PATH "C:/Development/Librarys/lib/libSDL2_gpu.dll.a")

#set(CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS}" )

target_link_libraries(SDL_Sandbox
#        -lmingw32
        ${SDL2_LIBRARY_MAIN}
        ${SDL2_LIBRARY}
        #        ${SDL2_IMAGE_LIBRARY}
        ${SDL_GPU_LIBRARY_PATH})

message(${SDL2_INCLUDE_DIR})
#message(${SDL2_IMAGE_LIBRARY})
message(${SDL_GPU_LIBRARY_PATH})
message(${SDL2_LIBRARY})
#message(${SDL2_LIBRARY_MAIN})
