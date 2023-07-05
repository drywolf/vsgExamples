set(SOURCES
    vsgcustompbr.cpp
    custom_pbr.cpp
)

# do not compile the custom_pbr.cpp file, just include it in the IDEs for easier navigation
set_source_files_properties(custom_pbr.cpp PROPERTIES HEADER_FILE_ONLY TRUE)

add_executable(vsgcustompbr ${SOURCES})

target_link_libraries(vsgcustompbr vsg::vsg)

if (vsgXchange_FOUND)
    target_compile_definitions(vsgcustompbr PRIVATE vsgXchange_FOUND)
    target_link_libraries(vsgcustompbr vsgXchange::vsgXchange)
endif()

install(TARGETS vsgcustompbr RUNTIME DESTINATION bin)

