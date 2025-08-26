# Glslang库配置文件

# 设置glslang库路径
set(GLSLANG_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64)
set(GLSLANG_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)

# 按功能分组管理glslang库
set(GLSLANG_CORE_LIBS
    ${GLSLANG_LIB_DIR}/glslang.lib
)

set(GLSLANG_RESOURCE_LIBS
    ${GLSLANG_LIB_DIR}/glslang-default-resource-limits.lib
)

# 创建glslang库目标
add_library(glslang_core INTERFACE)
target_link_libraries(glslang_core INTERFACE ${GLSLANG_CORE_LIBS})
target_include_directories(glslang_core INTERFACE ${GLSLANG_INCLUDE_DIR})

add_library(glslang_resource INTERFACE)
target_link_libraries(glslang_resource INTERFACE ${GLSLANG_RESOURCE_LIBS})
target_include_directories(glslang_resource INTERFACE ${GLSLANG_INCLUDE_DIR})

# 创建完整的glslang库目标
add_library(glslang INTERFACE)
target_link_libraries(glslang INTERFACE 
    glslang_core
    glslang_resource
)
target_include_directories(glslang INTERFACE ${GLSLANG_INCLUDE_DIR})

# 设置编译选项
target_compile_definitions(glslang INTERFACE
    _WIN32
    WIN32_LEAN_AND_MEAN
    NOMINMAX
)

# 设置运行时库
set_target_properties(glslang PROPERTIES
    MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
)
