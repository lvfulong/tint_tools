cmake_minimum_required(VERSION 3.16)
set(PROJECT_NAME tint_tools)
project(${PROJECT_NAME})

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

set(PROJECT_SOURCES)
set(PROJECT_DEPENDENCIES)
list(APPEND PROJECT_SOURCES
	./main.cc
)
add_executable(${PROJECT_NAME} ${PROJECT_SOURCES})

if (WIN32)
	list(APPEND PROJECT_SOURCES
	./main.cc
	)
	list(APPEND PROJECT_DEPENDENCIES
		ws2_32
	)
	set_target_properties(${PROJECT_NAME} PROPERTIES LINK_FLAGS "/SUBSYSTEM:CONSOLE")
endif()

# 添加tint库
add_subdirectory(third_party/tint)

# 使用方式1：链接完整的tint库（包含所有组件）
list(APPEND PROJECT_DEPENDENCIES tint)

# 使用方式2：按需链接特定组件（可选，取消注释使用）
# list(APPEND PROJECT_DEPENDENCIES 
#     tint_core      # 核心功能
#     tint_wgsl      # WGSL语言支持
#     tint_spirv     # SPIR-V支持
#     tint_glsl      # GLSL支持
#     tint_hlsl      # HLSL支持
#     tint_msl       # MSL支持
#     tint_utils     # 工具库
#     tint_api       # API接口
#     tint_cmd       # 命令行工具
# )

target_link_libraries(${PROJECT_NAME} PRIVATE ${PROJECT_DEPENDENCIES})

add_subdirectory(third_party)

