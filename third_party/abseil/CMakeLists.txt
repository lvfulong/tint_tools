# Abseil库配置文件

# 设置abseil库路径
set(ABSEIL_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64)
set(ABSEIL_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include/win-x64)

# 按功能分组管理abseil库
set(ABSEIL_BASE_LIBS
    ${ABSEIL_LIB_DIR}/absl_base.lib
    ${ABSEIL_LIB_DIR}/absl_throw_delegate.lib
    ${ABSEIL_LIB_DIR}/absl_raw_logging_internal.lib
    ${ABSEIL_LIB_DIR}/absl_log_severity.lib
    ${ABSEIL_LIB_DIR}/absl_spinlock_wait.lib
    ${ABSEIL_LIB_DIR}/absl_scoped_set_env.lib
    ${ABSEIL_LIB_DIR}/absl_poison.lib
    ${ABSEIL_LIB_DIR}/absl_strerror.lib
    ${ABSEIL_LIB_DIR}/absl_tracing_internal.lib
    ${ABSEIL_LIB_DIR}/absl_malloc_internal.lib
)

set(ABSEIL_STRINGS_LIBS
    ${ABSEIL_LIB_DIR}/absl_strings.lib
    ${ABSEIL_LIB_DIR}/absl_strings_internal.lib
    ${ABSEIL_LIB_DIR}/absl_string_view.lib
    ${ABSEIL_LIB_DIR}/absl_str_format_internal.lib
)

set(ABSEIL_CORD_LIBS
    ${ABSEIL_LIB_DIR}/absl_cord.lib
    ${ABSEIL_LIB_DIR}/absl_cord_internal.lib
    ${ABSEIL_LIB_DIR}/absl_cordz_info.lib
    ${ABSEIL_LIB_DIR}/absl_cordz_handle.lib
    ${ABSEIL_LIB_DIR}/absl_cordz_functions.lib
    ${ABSEIL_LIB_DIR}/absl_cordz_sample_token.lib
)

# 创建abseil库目标
add_library(abseil_base INTERFACE)
target_link_libraries(abseil_base INTERFACE ${ABSEIL_BASE_LIBS})
target_include_directories(abseil_base INTERFACE ${ABSEIL_INCLUDE_DIR})

add_library(abseil_strings INTERFACE)
target_link_libraries(abseil_strings INTERFACE ${ABSEIL_STRINGS_LIBS})
target_include_directories(abseil_strings INTERFACE ${ABSEIL_INCLUDE_DIR})

add_library(abseil_cord INTERFACE)
target_link_libraries(abseil_cord INTERFACE ${ABSEIL_CORD_LIBS})
target_include_directories(abseil_cord INTERFACE ${ABSEIL_INCLUDE_DIR})

# 创建完整的abseil库目标
add_library(abseil INTERFACE)
target_link_libraries(abseil INTERFACE 
    abseil_base
    abseil_strings
    abseil_cord
)
target_include_directories(abseil INTERFACE ${ABSEIL_INCLUDE_DIR})

# 设置编译选项
target_compile_definitions(abseil INTERFACE
    ABSL_USES_HASH=1
    _WIN32
    WIN32_LEAN_AND_MEAN
    NOMINMAX
)

# 设置运行时库
set_target_properties(abseil PROPERTIES
    MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>"
)
