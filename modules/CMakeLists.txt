# Websocketpp
add_library(websocketpp-HeaderOnly INTERFACE)
target_include_directories(websocketpp-HeaderOnly INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/websocketpp)

#Whispercpp
set(BUILD_SHARED_LIBS OFF)
add_subdirectory(whisper.cpp)