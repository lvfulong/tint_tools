cmake_minimum_required(VERSION 3.16)
set(PROJECT_NAME tint_tools)
project(${PROJECT_NAME})

set(CMAKE_C_STANDARD 99)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# 设置运行时库为静态库
if(MSVC)
    set(CMAKE_MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    add_compile_options(/utf-8)
    add_compile_options(/Zc:preprocessor)
    add_compile_options(/W3)
    add_compile_options(/wd4819)
    add_compile_options(/wd5109)
endif()

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
add_definitions(-DNOMINMAX)

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

# 添加第三方库
add_subdirectory(third_party/tint)
add_subdirectory(third_party/spirv-tools)
add_subdirectory(third_party/abseil)
add_subdirectory(third_party/glslang)

# 链接库
list(APPEND PROJECT_DEPENDENCIES tint)
list(APPEND PROJECT_DEPENDENCIES spirv-tools spirv-tools-opt)
list(APPEND PROJECT_DEPENDENCIES abseil)
list(APPEND PROJECT_DEPENDENCIES glslang)

target_link_libraries(${PROJECT_NAME} PRIVATE ${PROJECT_DEPENDENCIES})



