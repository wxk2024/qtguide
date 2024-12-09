cmake_minimum_required(VERSION 3.12)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if (MSVC)
    add_compile_options(/Zc:preprocessor /utf-8 /DNOMINMAX /D_USE_MATH_DEFINES /EHsc /bigobj)
else()
    if (WIN32)
        add_compile_options(-finput-charset=utf-8 -fexec-charset=utf-8)
    endif()
    add_compile_options(-Wall -Wextra -Werror=return-type)
endif()

project(01_9x9_table)

find_package(Qt5 REQUIRED COMPONENTS Core Widgets REQUIRED)

file(GLOB sources *.cpp)
add_executable(01_9x9_table ${sources})
target_link_libraries(01_9x9_table PRIVATE Qt5::Core Qt5::Widgets)
