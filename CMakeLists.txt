cmake_minimum_required(VERSION 3.17)
project(UTE)

set(CMAKE_CXX_STANDARD 17)

include_directories(ThirdParty/glfw/include/)
include_directories(Core/)
include_directories(ThirdParty/stb/)

add_subdirectory(ThirdParty/glfw)

add_executable(UntitledIDE ${IDESrc} main.cpp ThirdParty/stb/stb_image.h)

if(WIN32)
    target_link_libraries(UTE glfw opengl32 glew32)
elseif(APPLE)
    target_link_libraries(UTE glfw ${OPENGL_LIBRARIES} GLEW)
else()
    target_link_libraries(UTE glfw OpenGL GLEW)
endif()