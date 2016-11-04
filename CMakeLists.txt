cmake_minimum_required(VERSION 2.8.12)
project(tetgen)

add_library(tetgen STATIC tetgen.cxx predicates.cxx)
target_compile_definitions(tetgen PRIVATE -DTETLIBRARY)
if(UNIX)
    target_compile_options(tetgen PRIVATE -fPIC)
endif(UNIX)

ADD_EXECUTABLE(tetgen_bin tetgen.cxx predicates.cxx)
if(UNIX)
    target_compile_options(tetgen PRIVATE -fPIC)
endif(UNIX)

INSTALL(TARGETS tetgen
    LIBRARY DESTINATION lib
    ARCHIVE DESTINATION lib
    )
INSTALL(FILES tetgen.h DESTINATION include)
