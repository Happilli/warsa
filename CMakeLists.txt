cmake_minimum_required(VERSION 3.20)
project(warsa)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_AUTOMOC ON)

if(CMAKE_INSTALL_PREFIX_INITIALIZED_TO_DEFAULT)
  set(CMAKE_INSTALL_PREFIX "${CMAKE_BINARY_DIR}/install" CACHE PATH "Install path prefix" FORCE)
endif()

find_package(Qt6 REQUIRED COMPONENTS Core Qml)

set(QML_IMPORT_PATH "${CMAKE_INSTALL_PREFIX}" CACHE STRING "" FORCE)

qt_add_qml_module(warsa
  URI Warsa
    VERSION 1.0
    SOURCES
        warsa.cpp
        warsa.hpp
    NO_PLUGIN_OPTIONAL
    OUTPUT_DIRECTORY "${CMAKE_INSTALL_PREFIX}/Warsa"
)

target_link_libraries(warsa PRIVATE
    Qt6::Core
    Qt6::Qml
)
