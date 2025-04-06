if(NOT MU_IMPL)
    message(FATAL_ERROR "No implementation was selected. Options are: seq or std.")
endif()

# add compile definitions and external dependecies based on options
if ("${MU_IMPL}" STREQUAL "seq")
    add_subdirectory(implementations/sequential)
    add_compile_definitions(MU_ENABLE_SEQ)
elseif ("${MU_IMPL}" STREQUAL "std")
    add_subdirectory(implementations/std)
    add_compile_definitions(MU_ENABLE_STD)
else()
    message(FATAL_ERROR "${MU_IMPL} is not a valid configuration.")
endif ()

# set common properties
set_target_properties(muphys_implementation PROPERTIES LINKER_LANGUAGE CXX)
target_include_directories(muphys_implementation PUBLIC
                          "${PROJECT_BINARY_DIR}"
                          "${PROJECT_SOURCE_DIR}")                      