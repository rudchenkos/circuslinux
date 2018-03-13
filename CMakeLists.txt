cmake_minimum_required(VERSION 2.8)

find_package(PkgConfig REQUIRED)

pkg_check_modules(SDL REQUIRED sdl2 SDL2_image SDL2_mixer)

include_directories(${SDL_INCLUDE_DIRS})
link_directories(${SDL_LIBRARY_DIRS})

add_definitions(-D__MACOSX__ -DLINUX -DVERSION=\"1.0.0\" -DDATA_PREFIX=\"${PROJECT_SOURCE_DIR}/data/\")
add_compile_options(${SDL_CFLAGS})

add_executable(circuslinux circuslinux.c)
target_link_libraries(circuslinux ${SDL_LIBRARIES} ${SDL_LDFLAGS})
