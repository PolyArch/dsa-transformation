project(StreamSpecialization)

cmake_minimum_required(VERSION 3.12)

file(GLOB_RECURSE SRCS *.cpp)

add_library(StreamSpecialize SHARED ${SRCS})

target_include_directories(StreamSpecialize
  PRIVATE
  $ENV{SS_TOOLS}/include
  $ENV{SS}/dsa-llvm-project/include/llvm/)

execute_process(COMMAND llvm-config --libfiles
	OUTPUT_VARIABLE llvm_libs
	RESULT_VARIABLE __llvm_exit_code)
string(STRIP ${llvm_libs} llvm_libs)
separate_arguments(llvm_libs)

target_link_libraries(StreamSpecialize
  PRIVATE
  $ENV{SS_TOOLS}/lib/libdsa.so
  ${llvm_libs})

install(TARGETS StreamSpecialize DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
