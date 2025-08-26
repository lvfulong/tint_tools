

if (WIN32)
    add_library(spirv-tools INTERFACE)
    target_link_libraries(spirv-tools INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/SPIRV-Tools.lib)
    target_include_directories(spirv-tools INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)

    add_library(spirv-tools-opt INTERFACE)
    target_link_libraries(spirv-tools-opt INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/SPIRV-Tools-opt.lib)
    target_include_directories(spirv-tools-opt INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)
    
    # 设置编译选项
    target_compile_definitions(spirv-tools INTERFACE
        SPIRV_TOOLS_SHAREDLIB
    )
    
    target_compile_definitions(spirv-tools-opt INTERFACE
        SPIRV_TOOLS_SHAREDLIB
    )
    
    # 设置运行时库
    set_target_properties(spirv-tools PROPERTIES
        MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
    )
    
    set_target_properties(spirv-tools-opt PROPERTIES
        MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
    )
    
    message(STATUS "SPIRV-Tools libraries configured:")
    message(STATUS "  - spirv-tools: ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/SPIRV-Tools.lib")
    message(STATUS "  - spirv-tools-opt: ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64/SPIRV-Tools-opt.lib")
    message(STATUS "  - Include directory: ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64")
endif()
