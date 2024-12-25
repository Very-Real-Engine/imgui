cmake_minimum_required(VERSION 3.10)
project(ImGui LANGUAGES CXX)

add_library(imgui STATIC
    imconfig.h
    imgui.h
    imgui.cpp
    imgui_draw.cpp
    imgui_internal.h
    imgui_widgets.cpp
    imstb_rectpack.h
    imstb_textedit.h
    imstb_truetype.h
    imgui_demo.cpp
)

# ImGui 설치 구성
install(TARGETS imgui
    EXPORT imguiTargets
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
    RUNTIME DESTINATION bin
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/
    DESTINATION include/imgui
    FILES_MATCHING PATTERN "*.h"
)

# 설치용 CMake 파일 추가
install(EXPORT imguiTargets
    FILE imguiConfig.cmake
    DESTINATION lib/cmake/imgui
)