

if (WIN32)
    add_library(spirv-tools INTERFACE)
    target_link_libraries(spirv-tools INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/spirv-tools.lib)
    target_include_directories(spirv-tools INTERFACE${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)


    add_library(spirv-tools-opt INTERFACE)
    target_link_libraries(spirv-tools-opt INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/spirv-tools-opt.lib)
    target_include_directories(spirv-tools-opt INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)
    
endif()
