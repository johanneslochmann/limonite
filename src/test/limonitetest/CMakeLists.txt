cmake_minimum_required(VERSION 3.10)

project(limonitetest C CXX)

if(NOT MSVC)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
else()
  add_definitions(-D_WIN32_WINNT=0x600)
endif()

add_executable(limonitetest
  main.cxx
)

#target_link_libraries(limonitetest)
