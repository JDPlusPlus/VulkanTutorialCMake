cmake_minimum_required(VERSION 3.26)
project(VulkanTutorialCMake)
find_package(Vulkan REQUIRED)
set(${SOURCE_FILES}
        src/main.cpp
        )
include(FetchContent)
# Fetch GLFW and override find_package(glfw)
FetchContent_Declare(
        glfw
        GIT_REPOSITORY https://github.com/glfw/glfw.git
        GIT_TAG        3.4
        SOURCE_DIR ${CMAKE_SOURCE_DIR}/external/glfw
)
FetchContent_MakeAvailable(glfw)
find_package(Vulkan REQUIRED)

add_executable(${PROJECT_NAME} ${SOURCE_FILES} src/main.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE
        Vulkan::Vulkan
        glfw
        #glm
        )