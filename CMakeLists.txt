cmake_minimum_required(VERSION 3.20)
project(SpeechRecognition VERSION 1.0.0)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)


set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_subdirectory(modules)

find_package(SDL2 REQUIRED)
include_directories(${SDL2_INCLUDE_DIRS})

add_executable(ws-server ws-server.cpp 
    stream.cpp
    ${CMAKE_SOURCE_DIR}/modules/whisper.cpp/examples/common-ggml.cpp
    ${CMAKE_SOURCE_DIR}/modules/whisper.cpp/examples/common-sdl.cpp
    ${CMAKE_SOURCE_DIR}/modules/whisper.cpp/examples/common.cpp
)
target_link_libraries(ws-server PRIVATE 
    pthread
    websocketpp-HeaderOnly
    ${SDL2_LIBRARIES}
    whisper
    boost_system
    boost_thread
)

target_include_directories(ws-server PRIVATE ${CMAKE_SOURCE_DIR}/modules/whisper.cpp/examples)