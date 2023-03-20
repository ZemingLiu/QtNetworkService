cmake_minimum_required(VERSION 3.5)

project(QtNetworkService
    VERSION 1.1.0
    LANGUAGES CXX
)

find_package(QT NAMES Qt6 Qt5 REQUIRED COMPONENTS Core Network)
find_package(Qt${QT_VERSION_MAJOR} REQUIRED COMPONENTS Core Network)

set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)
if (QT_VERSION_MAJOR EQUAL 6)
    set(CMAKE_CXX_STANDARD 17 CACHE STRING "")
else()
    set(CMAKE_CXX_STANDARD 11 CACHE STRING "")
endif()
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(QtNetworkService
    HttpClient.h
)

target_link_libraries(QtNetworkService
    PUBLIC
        Qt${QT_VERSION_MAJOR}::Core
        Qt${QT_VERSION_MAJOR}::Network
)

target_include_directories(QtNetworkService
    INTERFACE
        "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}>"
)

target_compile_features(QtNetworkService INTERFACE cxx_std_11)
