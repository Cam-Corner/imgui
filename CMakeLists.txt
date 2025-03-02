cmake_minimum_required(VERSION 3.16)

project(imgui)

file(GLOB SOURCES 
    "imgui.cpp",
    "imgui_draw.cpp",
    "imgui_demo.cpp",
    "imgui_internal.cpp",
    "imgui_tables.cpp",
    "imgui_widgets.cpp",
    "backends/imgui_impl_sdl3.cpp",
    "backends/imgui_impl_opengl3.cpp"
)

file(GLOB HEADERS 
    "imconfig.h",
    "imgui.h",
    "imstb_rectpack.h",
    "imstb_textedit.h",
    "imstb_truetype.h",
    "backends/imgui_impl_sdl3.h",
    "backends/imgui_impl_opengl3.h"
)

# Add an executable target
add_library(imgui STATIC ${SOURCES} ${HEADERS})
target_include_directories(imgui PUBLIC 
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/backends
    )

# link sdl
link_directories(${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/SDL3/Debug)
target_include_directories(imgui PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/SDL3/include)
# find_package(SDL3 REQUIRED)
target_link_libraries(imgui PRIVATE SDL3-shared)

# Specify include directories for Glad

