set(SOURCES
    vsgcustompbr.cpp
    custom_pbr.cpp
)

# do not compile the custom_pbr.cpp file, just include it in the IDEs for easier navigation
set_source_files_properties(custom_pbr.cpp PROPERTIES HEADER_FILE_ONLY TRUE)

add_executable(vsgcustompbr ${SOURCES})

target_link_libraries(vsgcustompbr vsg::vsg)

# needed to include "custom_pbr.cpp"
target_include_directories(vsgcustompbr PRIVATE "${CMAKE_CURRENT_SOURCE_DIR}")

# needed to directly load files from "vsgExamples/data"
target_compile_definitions(vsgcustompbr PRIVATE "CMAKE_SOURCE_DIR=std::string(\"${CMAKE_SOURCE_DIR}\")")

if (vsgXchange_FOUND)
    target_compile_definitions(vsgcustompbr PRIVATE vsgXchange_FOUND)
    target_link_libraries(vsgcustompbr vsgXchange::vsgXchange)
endif()

install(TARGETS vsgcustompbr RUNTIME DESTINATION bin)

# always automatically load this FBX model for testing
set_target_properties(vsgcustompbr PROPERTIES VS_DEBUGGER_COMMAND_ARGUMENTS
    "${CMAKE_SOURCE_DIR}/data/models/fbx-test.fbx"
)
