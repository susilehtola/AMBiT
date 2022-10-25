cmake_minimum_required (VERSION 3.0)
project (AMBiT CXX Fortran)
set(CMAKE_CXX_STANDARD 11)

option(USE_OPENMP "Compile OpenMP enabled version (for parallel calculations)?" ON)

find_package(OpenMP)
if(OPENMP_FOUND)
  add_definitions(-DAMBIT_USE_OPENMP)
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS}")
endif()

find_package(Eigen3 REQUIRED)
find_package(GSL REQUIRED)
find_package(Boost COMPONENTS filesystem REQUIRED)
find_package(BLAS REQUIRED)
find_package(LAPACK REQUIRED)

# sparsehash doesn't have a CMake file
find_package(PkgConfig REQUIRED)
pkg_check_modules(libsparsehash REQUIRED)

# List all include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(${EIGEN3_INCLUDE_DIRS})
include_directories(${GSL_INCLUDE_DIRS})
include_directories(${BOOST_INCLUDE_DIRS})
include_directories(${libsparsehash_INCLUDE_DIRS})
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

# Compile code
add_subdirectory(Atom)
add_subdirectory(Basis)
add_subdirectory(Configuration)
add_subdirectory(ExternalField)
add_subdirectory(HartreeFock)
add_subdirectory(MBPT)
add_subdirectory(Universal)

