add_library(muphys_implementation SHARED "graupel.cpp")
target_link_libraries(muphys_implementation muphys_core tbb)