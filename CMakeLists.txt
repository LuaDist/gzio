# Copyright (C) 2007-2009 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

PROJECT(gzio C)
CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
INCLUDE(dist.cmake)

# Find Zlib
FIND_PACKAGE (ZLIB REQUIRED)
INCLUDE_DIRECTORIES( ${ZLIB_INCLUDE_DIR})

# Build
INCLUDE_DIRECTORIES(src)
ADD_LUA_MODULE(gzio src/lgziolib.c src/gzio.def)
TARGET_LINK_LIBRARIES(gzio ${ZLIB_LIBRARIES} )

# Install all files and documentation
INSTALL (TARGETS gzio DESTINATION ${INSTALL_CMOD})
INSTALL (FILES src/tar.lua DESTINATION ${INSTALL_LMOD})
INSTALL (FILES README DESTINATION ${INSTALL_DATA})
INSTALL (DIRECTORY test/ DESTINATION ${INSTALL_TEST})
