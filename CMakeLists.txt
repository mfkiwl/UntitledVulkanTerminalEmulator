cmake_minimum_required(VERSION 3.17)
project(UTE)

set(CMAKE_CXX_STANDARD 17)

include_directories(ThirdParty/glfw/include/)
include_directories(Core/)
include_directories(ThirdParty/stb/)

add_subdirectory(ThirdParty/glfw/)
add_subdirectory(ThirdParty/vulkan/)

add_executable(UTE ${IDESrc} main.cpp ThirdParty/stb/stb_image.h)
set_target_properties(PROPERTIES LINKER_LANGUAGE CXX)

if(WIN32)
    target_link_libraries(UTE glfw vulkan-1)
else()
    target_link_libraries(UTE glfw vulkan)
endif()