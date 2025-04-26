cmake_minimum_required(VERSION 3.26)

# CREATE PROJECT
project(ImNodeFlow)

add_compile_definitions(IMGUI_DEFINE_MATH_OPERATORS)

# SET SOURCE FILES FOR PROJECT
file(GLOB_RECURSE IMNODEFLOW_INCLUDE CMAKE_CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/include/*.h")
file(GLOB_RECURSE IMNODEFLOW_SOURCE "${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp" "${CMAKE_CURRENT_SOURCE_DIR}/src/*.h" "${CMAKE_CURRENT_SOURCE_DIR}/src/*.inl")

# ImGUI ############################################

set(IMGUI_PATH "../imgui")

set(IMGUI_INCLUDE
        "${IMGUI_PATH}/imconfig.h"
        "${IMGUI_PATH}/imgui.h"
        "${IMGUI_PATH}/imgui_internal.h"
        "${IMGUI_PATH}/imstb_rectpack.h"
        "${IMGUI_PATH}/imstb_textedit.h"
        "${IMGUI_PATH}/imstb_truetype.h"   
)
set(IMGUI_SOURCE
        "${IMGUI_PATH}/imgui.cpp"
        "${IMGUI_PATH}/imgui_demo.cpp"
        "${IMGUI_PATH}/imgui_draw.cpp"
        "${IMGUI_PATH}/imgui_tables.cpp"
        "${IMGUI_PATH}/imgui_widgets.cpp"  
)

####################################################



# CREATE LIBRARY FROM SOURCE_FILES
add_library(ImNodeFlow ${IMNODEFLOW_SOURCE})

# PREP TO USE "#include <>"
target_include_directories(ImNodeFlow PUBLIC Include )
target_include_directories(ImNodeFlow PUBLIC ${IMGUI_PATH} )
target_sources(ImNodeFlow PUBLIC ${IMGUI_SOURCE})
