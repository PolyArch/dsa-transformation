cmake_minimum_required(VERSION 3.12)

file(GLOB_RECURSE SRCS *.cpp)

add_library(StreamSpecialize SHARED ${SRCS})

find_package(LLVM REQUIRED)

target_include_directories(StreamSpecialize
  PRIVATE
  $ENV{SS_TOOLS}/include
  $ENV{SS}/ss-llvm/include/llvm/)

link_directories($ENV{SS_TOOLS}/lib)

target_link_libraries(StreamSpecialize
  PRIVATE
  $ENV{SS_TOOLS}/lib/libssscheduler.so
  $ENV{SS_TOOLS}/lib/libssconfig.so
  ${llvm_libs})
