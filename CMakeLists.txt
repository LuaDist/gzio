# Copyright (C) 2007-2012 LuaDist.
# Created by Peter Kapec
# Redistribution and use of this file is allowed according to the terms of the MIT license.
# For details see the COPYRIGHT file distributed with LuaDist.
# Please note that the package source code is licensed under its own license.

project ( gzio C )
cmake_minimum_required ( VERSION 2.8 )
include ( cmake/dist.cmake )
include ( lua )

# Find Zlib
find_package ( ZLIB REQUIRED )
include_directories ( ${ZLIB_INCLUDE_DIR} )

include_directories ( src )
install_lua_module ( gzio src/lgziolib.c src/gzio.def )
target_link_libraries ( gzio ${ZLIB_LIBRARIES} )

install_lua_module ( tar src/tar.lua )
install_data ( README )
install_test ( test/ )

add_lua_test ( test/test.lua test )
add_lua_test ( test/lartest.lua test )
add_lua_test ( test/tartest.lua test )
configure_file ( test/testdir.tar.gz ${CMAKE_CURRENT_BINARY_DIR}/testdir.tar.gz COPYONLY )
configure_file ( test/test.txt ${CMAKE_CURRENT_BINARY_DIR}/test.txt COPYONLY )
configure_file ( test/lar.lua ${CMAKE_CURRENT_BINARY_DIR}/lar.lua COPYONLY )
