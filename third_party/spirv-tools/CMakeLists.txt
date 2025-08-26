

if (WIN32)
    set(SPIRV_TOOLS_LIBS ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/spirv-tools.lib)
    set(SPIRV_TOOLS_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)
    
    add_library(spirv-tools INTERFACE)
    target_link_libraries(spirv-tools INTERFACE ${SPIRV_TOOLS_LIBS})
    target_include_directories(spirv-tools INTERFACE ${SPIRV_TOOLS_INCLUDE_DIR})
endif()
