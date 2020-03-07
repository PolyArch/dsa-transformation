cmake_minimum_required(VERSION 3.12)

add_library(StreamSpecialize SHARED
  DfgEntry.cpp
  DfgInfo.cpp
  StreamSpecialize.cpp
  Util.cpp)

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
  LLVMXRay 
  LLVMWindowsManifest 
  LLVMTableGen 
  LLVMSymbolize 
  LLVMDebugInfoPDB 
  LLVMOrcJIT 
  LLVMJITLink 
  LLVMObjectYAML 
  LLVMMIRParser 
  LLVMMCJIT 
  LLVMMCA 
  LLVMLTO 
  LLVMPasses 
  LLVMObjCARCOpts 
  LLVMLineEditor 
  LLVMLibDriver 
  LLVMFuzzMutate 
  LLVMInterpreter 
  LLVMExecutionEngine 
  LLVMRuntimeDyld 
  LLVMDlltoolDriver 
  LLVMOption 
  LLVMDebugInfoGSYM 
  LLVMCoverage 
  LLVMCoroutines 
  LLVMipo 
  LLVMInstrumentation 
  LLVMVectorize 
  LLVMLinker 
  LLVMIRReader 
  LLVMAsmParser 
  LLVMRISCVDisassembler 
  LLVMMCDisassembler 
  LLVMRISCVCodeGen 
  LLVMGlobalISel 
  LLVMSelectionDAG 
  LLVMAsmPrinter 
  LLVMDebugInfoDWARF 
  LLVMCodeGen 
  LLVMTarget 
  LLVMScalarOpts 
  LLVMInstCombine 
  LLVMAggressiveInstCombine 
  LLVMTransformUtils 
  LLVMBitWriter 
  LLVMAnalysis 
  LLVMProfileData 
  LLVMObject 
  LLVMTextAPI 
  LLVMBitReader 
  LLVMCore 
  LLVMRemarks 
  LLVMBitstreamReader 
  LLVMRISCVAsmParser 
  LLVMMCParser 
  LLVMRISCVDesc 
  LLVMMC 
  LLVMDebugInfoCodeView 
  LLVMDebugInfoMSF 
  LLVMBinaryFormat 
  LLVMRISCVUtils 
  LLVMRISCVInfo 
  LLVMSupport 
  LLVMDemangle)
