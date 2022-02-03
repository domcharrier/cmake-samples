project(FindHipLibraries Fortran C CXX)

set(EXTRA_LIBRARIES)

# CHAMELEON depends on HIP/HIPBLAS
#----------------------------------
find_package(hip REQUIRED)

message("-- ${Blue}Add definition CHAMELEON_USE_HIP"
" - Activate HIP in Chameleon${ColourReset}")
set(EXTRA_LIBRARIES_HIP)
set(CHAMELEON_USE_HIP 1)
#if(HIP_VERSION VERSION_LESS "3.0")
#    set(HIP_HOST_COMPILATION_CPP OFF)
#endif(HIP_VERSION VERSION_LESS "3.0")
set(HIP_BUILD_EMULATION OFF)
set(HIP_HAVE_PEER_DEVICE_MEMORY_ACCESS 1)

find_package(hipblas REQUIRED)

message("-- ${Blue}Add definition CHAMELEON_USE_HIPBLAS"
" - Use GPU kernels from hipblas${ColourReset}")
set( CHAMELEON_USE_HIPBLAS 1)
list(APPEND EXTRA_LIBRARIES_HIP ${HIPBLAS_LIBRARIES})
list(APPEND EXTRA_LIBRARIES_HIP ${HIP_LIBRARIES}) # need HIP libs to link.

list(APPEND EXTRA_LIBRARIES ${EXTRA_LIBRARIES_HIP})

message("${EXTRA_LIBRARIES}")
