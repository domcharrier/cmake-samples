project(FindHIPTest Fortran C CXX)

find_package(hip REQUIRED)
find_package(hipblas REQUIRED)

message("hip_FOUND ${hip_FOUND}")
message("HIP_LIBRARIES ${HIP_LIBRARIES}")
message("HIP_LIBRARY_DIRS ${HIP_LIBRARY_DIRS}")

message("hipblas_FOUND ${hipblas_FOUND}")
message("HIPBLAS_LIBRARIES ${HIPBLAS_LIBRARIES}")
message("HIPBLAS_LIBRARY_DIRS ${HIPBLAS_LIBRARY_DIRS}")

#find_package(hipblasss) # will not continue if cannot find package
