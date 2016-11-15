cmake_minimum_required(VERSION 2.8.12)

set(TARGET_NAME "z")

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
target_include_directories(${TARGET_NAME} PUBLIC ".")
target_compile_definitions(${TARGET_NAME} PUBLIC ZLIB_CONST)
if(BUILD_SHARED_LIBS)
  target_compile_definitions(${TARGET_NAME} PUBLIC ZLIB_DLL)
endif()

if(BUILD_SHARED_LIBS)
  install(TARGETS ${TARGET_NAME}
        RUNTIME DESTINATION ./
        LIBRARY DESTINATION ./ COMPONENT "binaries")
endif()
