cmake_minimum_required(VERSION 3.10)

project(limonite CXX)

include(ExternalProject)

ExternalProject_Add(
    catch2
    PREFIX ${CMAKE_BINARY_DIR}/thirdparty/catch2
    GIT_REPOSITORY https://github.com/catchorg/Catch2.git
    TIMEOUT 10
    UPDATE_COMMAND ${GIT_EXECUTABLE} pull
    CONFIGURE_COMMAND ""
    BUILD_COMMAND ""
    INSTALL_COMMAND ""
    LOG_DOWNLOAD ON
   )

# Expose required variable (CATCH_INCLUDE_DIR) to parent scope
ExternalProject_Get_Property(catch2 source_dir)
set(CATCH2_INCLUDE_DIR ${source_dir}/include CACHE INTERNAL "Path to include folder for Catch2")

ExternalProject_Add(limonitetest
  PREFIX limonitetest
  SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/src/test/limonitetest"
  BINARY_DIR "${CMAKE_CURRENT_BINARY_DIR}/limonitetest"
  INSTALL_COMMAND ""
 )
