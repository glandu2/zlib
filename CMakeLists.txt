cmake_minimum_required(VERSION 2.8)

set(TARGET_NAME "z")
set(Z_INCLUDE "${CMAKE_CURRENT_LIST_DIR}" CACHE STRING "zlib include directory")

if(BUILD_SHARED_LIBS)
  add_definitions(-DZLIB_DLL)
endif()

set(SOURCE_FILES
  adler32.c
  compress.c
  crc32.c
  crc32.h
  deflate.c
  deflate.h
  inffast.c
  inffast.h
  inffixed.h
  inflate.c
  inflate.h
  inftrees.c
  inftrees.h
  trees.c
  trees.h
  uncompr.c
  zconf.h
  zlib.h
  zutil.c
  zutil.h
)

add_library(${TARGET_NAME} ${SOURCE_FILES})

if(BUILD_SHARED_LIBS)
  install(TARGETS ${TARGET_NAME}
        RUNTIME DESTINATION ./
        LIBRARY DESTINATION ./)
endif()
