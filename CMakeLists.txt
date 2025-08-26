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


add_definitions(-DTINT_BUILD_GLSL_VALIDATOR=1)
add_definitions(-DTINT_BUILD_GLSL_WRITER=1)
add_definitions(-DTINT_BUILD_HLSL_WRITER=1)
add_definitions(-DTINT_BUILD_IR_BINARY=0)
add_definitions(-DTINT_BUILD_MSL_WRITER=1)
add_definitions(-DTINT_BUILD_SPV_READER=1)
add_definitions(-DTINT_BUILD_SPV_WRITER=1)
add_definitions(-DTINT_BUILD_WGSL_READER=1)
add_definitions(-DTINT_BUILD_WGSL_WRITER=1)
add_definitions(-DTINT_BUILD_TINTD=0)
add_definitions(-DTINT_ENABLE_IR_VALIDATION=0)


if (WIN32)
    add_definitions(-DTINT_BUILD_IS_LINUX=0)
    add_definitions(-DTINT_BUILD_IS_MAC=0)
    add_definitions(-DTINT_BUILD_IS_WIN=1)
	list(APPEND PROJECT_SOURCES
		./main.cc
	)
	list(APPEND PROJECT_DEPENDENCIES
		kernel32.lib
		user32.lib
		gdi32.lib
		winspool.lib
		shell32.lib
		ole32.lib
		oleaut32.lib
		uuid.lib
	    comdlg32.lib
	    advapi32.lib
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

add_subdirectory(third_party/spirv-tools)
list(APPEND PROJECT_DEPENDENCIES spirv-tools spirv-tools-opt)




target_link_libraries(${PROJECT_NAME} PRIVATE ${PROJECT_DEPENDENCIES})



