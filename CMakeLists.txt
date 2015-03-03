cmake_minimum_required(VERSION 2.6.4)

project(webstor)

add_library(webstor STATIC
	asyncurl.cpp
	sysutils.cpp
	wscmd.cpp
	wsconn.cpp
	wsdbg.cpp
	wsperf.cpp
)
SET(CMAKE_CXX_FLAGS "-Wno-enum-compare")

# curl
find_package(CURL REQUIRED)
include_directories(${CURL_INCLUDE_DIRS})
target_link_libraries(webstor ${CURL_LIBRARIES})

# OpenSSL
find_package(OpenSSL REQUIRED)
include_directories(${OPENSSL_INCLUDE_DIR})
target_link_libraries(webstor ${OPENSSL_LIBRARIES})

# libxml2
find_package(LibXml2 REQUIRED)
include_directories(${LIBXML2_INCLUDE_DIR})
target_link_libraries(webstor ${LIBXML2_LIBRARIES})
