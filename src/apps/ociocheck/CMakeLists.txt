file(GLOB_RECURSE share_src_files "${CMAKE_SOURCE_DIR}/src/apps/share/*.cpp")

include_directories(
    ${CMAKE_SOURCE_DIR}/export/
    ${CMAKE_BINARY_DIR}/export/
    ${CMAKE_SOURCE_DIR}/src/apps/share/
    ${Boost_INCLUDE_DIR}
    )

add_executable(ociocheck
    main.cpp
    ${share_src_files})

set_target_properties(ociocheck PROPERTIES COMPILE_FLAGS -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE})

target_link_OCIO(ociocheck)

install(TARGETS ociocheck EXPORT OpenColorIO DESTINATION ${CMAKE_INSTALL_EXEC_PREFIX}/bin)
