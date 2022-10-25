add_library(Atom OBJECT Atom.cpp Atom_Open.cpp Atom_Autoionization.cpp
OutStreams.cpp)

add_executable(ambit ambit.cpp)

target_link_libraries(ambit Atom Basis Configuration ExternalField
HartreeFock MBPT Universal)

target_link_libraries(ambit ${Boost_FILESYSTEM_LIBRARY}
${GSL_LIBRARIES} ${libsparsehash_LIBRARIES} ${LAPACK_LIBRARIES}
${BLAS_LIBRARIES})

install(TARGETS ambit DESTINATION bin)
