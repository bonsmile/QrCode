cmake_minimum_required( VERSION 3.16.0 )

project(QrCode VERSION 1.0.0.21)

set(VERSION_RC ${CMAKE_CURRENT_SOURCE_DIR}/version.rc)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/dll.rc.in
                ${VERSION_RC}
                NEWLINE_STYLE UNIX)

message(CMAKE_PREFIX_PATH:${CMAKE_PREFIX_PATH})

add_library( QrCode SHARED
	QrCode.hpp
	QrCode.cpp
	${VERSION_RC}
)

target_compile_options( QrCode PRIVATE "/utf-8" "/MP" )
target_compile_definitions( QrCode PUBLIC -DBUILDING_DLL )
target_compile_definitions( QrCode PRIVATE -DUNICODE -D_UNICODE )
target_compile_features( QrCode PRIVATE cxx_std_17 )
