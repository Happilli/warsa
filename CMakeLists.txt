cmake_minimum_required(VERSION 3.20)
project(warsa)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_AUTOMOC ON)
find_package(Qt6 REQUIRED COMPONENTS Core Qml)

qt_add_qml_module(warsa
  URI Warsa
  VERSION 1.0
  SOURCES
      warsa.cpp
      warsa.hpp
  NO_PLUGIN_OPTIONAL
  OUTPUT_DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/Warsa"
)

target_link_libraries(warsa PRIVATE
    Qt6::Core
    Qt6::Qml
)

set(QML_INSTALL_DIR lib/qt6/qml/Warsa)

install(TARGETS warsa
    LIBRARY DESTINATION lib
)

install(TARGETS warsaplugin
    LIBRARY DESTINATION ${QML_INSTALL_DIR}
)

install(DIRECTORY "${CMAKE_CURRENT_BINARY_DIR}/Warsa/"
    DESTINATION ${QML_INSTALL_DIR}
    FILES_MATCHING
    PATTERN "*.qmltypes"
    PATTERN "qmldir"
    PATTERN "*.qrc"
)
