cmake_minimum_required (VERSION 3.2)
project(libEmuDeMIDI C CXX)

set(EMIDI_SRC
    src/CEnvelope.cpp
    src/CSMF.cpp
    src/device/emu2413.c
    src/device/emu2212.c
    src/device/emu2149.c
    src/CMIDIModule.cpp
    src/CSccDevice.cpp
    src/CPSGDrum.cpp
    src/CMIDIMessage.cpp
    src/COpllDevice.cpp
    src/CSMFPlay.cpp
)

if(WIN32)
    set(EMIDI_EXE_SRC utils/main_sdl.cpp)
else()
    set(EMIDI_EXE_SRC utils/main_sdl.cpp)
endif()

add_executable(emidi ${EMIDI_SRC} ${EMIDI_EXE_SRC})
target_include_directories(emidi PRIVATE src)

if(WIN32)
    target_link_libraries(emidi PUBLIC winmm user32 gdi32)
else()
    target_link_libraries(emidi PUBLIC SDL2)
endif()
