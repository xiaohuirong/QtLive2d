cmake_minimum_required(VERSION 3.10)

project(Demo VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

find_package(Qt6 REQUIRED COMPONENTS OpenGLWidgets)
find_package(CubismFramework REQUIRED)
find_package(Live2dWidget REQUIRED)

include_directories(${CMAKE_BINARY_DIR} 
                    ${CMAKE_SOURCE_DIR} 
                    ${CubismFramework_INCLUDE_DIRS} 
                    ${Live2dWidget_INCLUDE_DIRS})

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

set(SOURCES
    main.cpp
    mainwindow.cpp
)

set(HEADERS
    mainwindow.h
)

set(UIS
    mainwindow.ui
)

add_executable(${PROJECT_NAME} ${SOURCES} ${HEADERS} ${UIS})

target_link_libraries(${PROJECT_NAME} 
                      Qt6::Widgets Qt6::OpenGLWidgets 
                      ${Live2dWidget_LIBRARIES} 
                      ${CubismFramework_LIBRARIES})

set_target_properties(${PROJECT_NAME} PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)
