add_executable(cli
    cli.cpp
    playback.cpp
    playback.h
    write_file.cpp
    write_file.h
)

find_package(SDL2 REQUIRED CONFIG REQUIRED COMPONENTS SDL2)
if (SDL2_FOUND)
    target_link_libraries(cli PRIVATE SDL2::SDL2)
    set_source_files_properties(playback.cpp PROPERTIES COMPILE_FLAGS -DSDL2_INSTALL=1)
endif()

target_link_libraries(cli PRIVATE ggml tts)
