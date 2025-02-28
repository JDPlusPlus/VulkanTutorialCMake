cmake_minimum_required(VERSION 3.26)
project(VulkanTutorialCMake)
include(FetchContent)
find_package(Vulkan REQUIRED)
set(${SOURCE_FILES}
        src/main.cpp
        )
# Disable GLFW building non-essential glfw projects
set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

FetchContent_Declare(
        glfw
        GIT_REPOSITORY https://github.com/glfw/glfw.git
        GIT_TAG        3.4 # You MAY want to change this to the latest release version
        SOURCE_DIR ${CMAKE_SOURCE_DIR}/external/glfw
)
FetchContent_MakeAvailable(glfw)
FetchContent_Declare(
        glm
        GIT_REPOSITORY https://github.com/g-truc/glm.git
        GIT_TAG        1.0.1 # You MAY want to change this to the latest release version
        SOURCE_DIR ${CMAKE_SOURCE_DIR}/external/glm
)
FetchContent_MakeAvailable(glm)
find_package(Vulkan REQUIRED)

add_executable(${PROJECT_NAME} ${SOURCE_FILES} src/main.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE
        Vulkan::Vulkan
        glfw
        glm
        )