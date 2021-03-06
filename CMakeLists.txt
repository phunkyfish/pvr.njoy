cmake_minimum_required(VERSION 3.5)
project(pvr.njoy)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

find_package(TinyXML REQUIRED)
find_package(Kodi REQUIRED)
find_package(kodiplatform REQUIRED)
find_package(p8-platform REQUIRED)

include_directories(${kodiplatform_INCLUDE_DIRS}
                    ${p8-platform_INCLUDE_DIRS}
                    ${TINYXML_INCLUDE_DIR}
                    ${KODI_INCLUDE_DIR}/..) # Hack way with "/..", need bigger Kodi cmake rework to match right include ways

set(NJOY_SOURCES src/client.cpp
                 src/N7Xml.cpp)

set(NJOY_HEADERS src/client.h
                 src/N7Xml.h)

set(DEPLIBS ${kodiplatform_LIBRARIES}
            ${p8-platform_LIBRARIES}
            ${TINYXML_LIBRARIES})

build_addon(pvr.njoy NJOY DEPLIBS)

include(CPack)
