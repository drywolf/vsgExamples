set(SOURCES
    vsgcustompbr.cpp
)

add_executable(vsgcustompbr ${SOURCES})

target_link_libraries(vsgcustompbr vsg::vsg)

if (vsgXchange_FOUND)
    target_compile_definitions(vsgcustompbr PRIVATE vsgXchange_FOUND)
    target_link_libraries(vsgcustompbr vsgXchange::vsgXchange)
endif()

install(TARGETS vsgcustompbr RUNTIME DESTINATION bin)

