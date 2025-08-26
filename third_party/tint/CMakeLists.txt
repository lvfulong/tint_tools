# Tint库配置文件
# 这个文件用于管理所有的tint库文件

# 设置tint库路径
set(TINT_LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/lib/win-x64)
set(TINT_INCLUDE_DIR ${CMAKE_CURRENT_SOURCE_DIR}/include)

# 自动发现所有tint库文件
file(GLOB TINT_ALL_LIBS "${TINT_LIB_DIR}/*.lib")

# 按功能分组管理tint库
set(TINT_CORE_LIBS
    ${TINT_LIB_DIR}/tint_lang_core.lib
    ${TINT_LIB_DIR}/tint_lang_core_ir.lib
    ${TINT_LIB_DIR}/tint_lang_core_type.lib
    ${TINT_LIB_DIR}/tint_lang_core_constant.lib
    ${TINT_LIB_DIR}/tint_lang_core_intrinsic.lib
    ${TINT_LIB_DIR}/tint_lang_core_ir_transform.lib
    ${TINT_LIB_DIR}/tint_lang_core_ir_analysis.lib
    ${TINT_LIB_DIR}/tint_lang_core_ir_type.lib
)

set(TINT_WGSL_LIBS
    ${TINT_LIB_DIR}/tint_lang_wgsl.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_reader.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_writer.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_ir.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_program.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_sem.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_ast.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_intrinsic.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_inspector.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_reader_parser.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_reader_lower.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_reader_program_to_ir.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_resolver.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_writer_raise.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_writer_ir_to_program.lib
    ${TINT_LIB_DIR}/tint_lang_wgsl_writer_ast_printer.lib
)

set(TINT_SPIRV_LIBS
    ${TINT_LIB_DIR}/tint_lang_spirv.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_writer.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_reader.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_ir.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_type.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_intrinsic.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_validate.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_writer_printer.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_writer_raise.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_writer_helpers.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_writer_common.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_reader_ast_parser.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_reader_parser.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_reader_lower.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_reader_ast_lower.lib
    ${TINT_LIB_DIR}/tint_lang_spirv_reader_common.lib
)

set(TINT_GLSL_LIBS
    ${TINT_LIB_DIR}/tint_lang_glsl.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_writer.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_ir.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_type.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_intrinsic.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_validate.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_writer_printer.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_writer_raise.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_writer_helpers.lib
    ${TINT_LIB_DIR}/tint_lang_glsl_writer_common.lib
)

set(TINT_HLSL_LIBS
    ${TINT_LIB_DIR}/tint_lang_hlsl.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_writer.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_ir.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_type.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_intrinsic.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_validate.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_writer_printer.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_writer_raise.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_writer_helpers.lib
    ${TINT_LIB_DIR}/tint_lang_hlsl_writer_common.lib
)

set(TINT_MSL_LIBS
    ${TINT_LIB_DIR}/tint_lang_msl.lib
    ${TINT_LIB_DIR}/tint_lang_msl_writer.lib
    ${TINT_LIB_DIR}/tint_lang_msl_ir.lib
    ${TINT_LIB_DIR}/tint_lang_msl_type.lib
    ${TINT_LIB_DIR}/tint_lang_msl_intrinsic.lib
    ${TINT_LIB_DIR}/tint_lang_msl_validate.lib
    ${TINT_LIB_DIR}/tint_lang_msl_writer_printer.lib
    ${TINT_LIB_DIR}/tint_lang_msl_writer_raise.lib
    ${TINT_LIB_DIR}/tint_lang_msl_writer_helpers.lib
    ${TINT_LIB_DIR}/tint_lang_msl_writer_common.lib
    ${TINT_LIB_DIR}/tint_lang_msl_ir_transform.lib
)

set(TINT_UTILS_LIBS
    ${TINT_LIB_DIR}/tint_utils.lib
    ${TINT_LIB_DIR}/tint_utils_text.lib
    ${TINT_LIB_DIR}/tint_utils_system.lib
    ${TINT_LIB_DIR}/tint_utils_file.lib
    ${TINT_LIB_DIR}/tint_utils_command.lib
    ${TINT_LIB_DIR}/tint_utils_diagnostic.lib
    ${TINT_LIB_DIR}/tint_utils_symbol.lib
    ${TINT_LIB_DIR}/tint_utils_strconv.lib
    ${TINT_LIB_DIR}/tint_utils_containers.lib
    ${TINT_LIB_DIR}/tint_utils_rtti.lib
    ${TINT_LIB_DIR}/tint_utils_memory.lib
    ${TINT_LIB_DIR}/tint_utils_ice.lib
    ${TINT_LIB_DIR}/tint_utils_math.lib
    ${TINT_LIB_DIR}/tint_utils_macros.lib
    ${TINT_LIB_DIR}/tint_utils_bytes.lib
    ${TINT_LIB_DIR}/tint_utils_text_generator.lib
)

set(TINT_API_LIBS
    ${TINT_LIB_DIR}/tint_api.lib
    ${TINT_LIB_DIR}/tint_api_common.lib
)

set(TINT_CMD_LIBS
    ${TINT_LIB_DIR}/tint_cmd_common.lib
    ${TINT_LIB_DIR}/tint_cmd_fuzz_ir_helpers.lib
)

# 创建tint库目标
add_library(tint_core INTERFACE)
target_link_libraries(tint_core INTERFACE ${TINT_CORE_LIBS})
target_include_directories(tint_core INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_wgsl INTERFACE)
target_link_libraries(tint_wgsl INTERFACE ${TINT_WGSL_LIBS})
target_include_directories(tint_wgsl INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_spirv INTERFACE)
target_link_libraries(tint_spirv INTERFACE ${TINT_SPIRV_LIBS})
target_include_directories(tint_spirv INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_glsl INTERFACE)
target_link_libraries(tint_glsl INTERFACE ${TINT_GLSL_LIBS})
target_include_directories(tint_glsl INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_hlsl INTERFACE)
target_link_libraries(tint_hlsl INTERFACE ${TINT_HLSL_LIBS})
target_include_directories(tint_hlsl INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_msl INTERFACE)
target_link_libraries(tint_msl INTERFACE ${TINT_MSL_LIBS})
target_include_directories(tint_msl INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_utils INTERFACE)
target_link_libraries(tint_utils INTERFACE ${TINT_UTILS_LIBS})
target_include_directories(tint_utils INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_api INTERFACE)
target_link_libraries(tint_api INTERFACE ${TINT_API_LIBS})
target_include_directories(tint_api INTERFACE ${TINT_INCLUDE_DIR})

add_library(tint_cmd INTERFACE)
target_link_libraries(tint_cmd INTERFACE ${TINT_CMD_LIBS})
target_include_directories(tint_cmd INTERFACE ${TINT_INCLUDE_DIR})

# 创建完整的tint库目标
add_library(tint INTERFACE)
target_link_libraries(tint INTERFACE 
    tint_core
    tint_wgsl
    tint_spirv
    tint_glsl
    tint_hlsl
    tint_msl
    tint_utils
    tint_api
    tint_cmd
)
target_include_directories(tint INTERFACE ${TINT_INCLUDE_DIR})
