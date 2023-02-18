#Based of: https://github.com/0xeb/detours-cmake

cmake_minimum_required(VERSION 3.5)

project(detours LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)

set(SOURCE_DIR ${CMAKE_SOURCE_DIR}/src)

set(SOURCE_FILES 
    ${SOURCE_DIR}/creatwth.cpp
    ${SOURCE_DIR}/detours.cpp
    ${SOURCE_DIR}/detours.h
    ${SOURCE_DIR}/detver.h
    ${SOURCE_DIR}/disasm.cpp
    ${SOURCE_DIR}/disolarm.cpp
    ${SOURCE_DIR}/disolarm64.cpp
    ${SOURCE_DIR}/disolia64.cpp
    ${SOURCE_DIR}/disolx64.cpp
    ${SOURCE_DIR}/disolx86.cpp
    ${SOURCE_DIR}/image.cpp
    ${SOURCE_DIR}/modules.cpp
    ${SOURCE_DIR}/uimports.cpp
)

add_library(${PROJECT_NAME} STATIC ${SOURCE_FILES})

set_property(
    SOURCE ${SOURCE_DIR}/uimports.cpp
    APPEND PROPERTY HEADER_FILE_ONLY true
)

target_compile_options(${PROJECT_NAME} PRIVATE /W4 /WX /Zi /MT /Gy /Gm- /Zl /Od)
target_include_directories(${PROJECT_NAME} PUBLIC ${SOURCE_DIR})
