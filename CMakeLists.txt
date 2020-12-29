cmake_minimum_required(VERSION 3.12)
project(libfoo VERSION 1.0.0 DESCRIPTION "Test library foo")
add_library(foo SHARED)
target_sources(foo PRIVATE foo.c)
set_target_properties(foo PROPERTIES VERSION ${CMAKE_PROJECT_VERSION})
set_target_properties(foo PROPERTIES SOVERSION ${CMAKE_PROJECT_VERSION_MAJOR})
set_target_properties(foo PROPERTIES PUBLIC_HEADER foo.h)

include(GNUInstallDirs)
install(TARGETS foo
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/foo
)
configure_file(libfoo.pc.in libfoo.pc @ONLY)
install(FILES ${CMAKE_BINARY_DIR}/libfoo.pc DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
