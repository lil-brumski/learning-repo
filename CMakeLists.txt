‎if(CMAKE_SOURCE_DIR STREQUAL CMAKE_BINARY_DIR)
‎    message(FATAL "You can't build in the same directory as the CMakeLists.txt file, create another directory and run `cmake ..` there.")
‎endif()
‎
‎cmake_minimum_required(VERSION 3.25.3)
‎
‎project(CMakeTemplate VERSION 0.0.1 LANGUAGES CXX DESCRIPTION "Text.")
‎
‎set(CMAKE_CXX_STANDARD 23)
‎set(CMAKE_CXX_STANDARD_REQUIRED True)
‎set(CMAKE_CXX_EXTENSIONS OFF)
‎set(CMAKE_BUILD_TYPE Release)
‎set(CMAKE_EXE_LINKER_FLAGS_RELEASE "-s")
‎
‎if(ANDROID)
‎   message(STATUS "==========Building for Android platform==========")
‎elseif(WIN32)
‎   message(STATUS "=========Building for Windows platform==========")
‎elseif(UNIX)
‎   if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
‎      message(STATUS "==========Building for Linux==========")
‎   elseif(CMAKE_SYSTEM_NAME STREQUAL "Darwin")
‎      message(STATUS "==========Building for MacOS==========")
‎   else()
‎      message(STATUS "==========Building for Unknown UNIX platform==========") 
‎    endif()
‎else()
‎     message(STATUS "==========Building for unknown platform==========")
‎endif()
‎
‎if(CMAKE_CXX_COMPILER_ID STREQUAL "Clang")
‎    message(STATUS "==========Configuring for Clang==========")
‎elseif(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
‎    message(STATUS "==========Configuring for GNU==========")
‎elseif(CMAKE_CXX_COMPILER_ID STREQUAL "MSVC")
‎    message(STATUS "==========Configuring for MSVC==========")
‎else()
‎    message(STATUS "Configuring for unknown compiler.")
‎endif()
‎
‎set(SOURCES
‎    src/file.cpp
‎    ...
‎    src/file2.cpp
‎)
‎
‎add_executable(${PROJECT_NAME} ${SOURCES})
‎
‎target_include_directories(${PROJECT_NAME} PRIVATE include)
‎
‎option(ProjectOption "BLAH BLAH" OFF)
‎
‎if(ProjectOption)
‎   if(CMAKE_CXX_COMPILER_ID STREQUAL "GNU")
‎       message(STATUS "==========Compiling for GNU statically==========")
‎       set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -static -Wall -Wextra -Werror")
‎   else()
‎       message(FATAL_ERROR "==========Error, current compiler isn't GNU!==========")
‎   endif()
‎endif()