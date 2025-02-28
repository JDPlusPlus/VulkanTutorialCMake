cmake_minimum_required(VERSION 3.26)
project(VulkanTutorialCMake)
find_package(Vulkan REQUIRED)
set(${SOURCE_FILES}
        src/main.cpp
        )

add_executable(${PROJECT_NAME} ${SOURCE_FILES} src/main.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE
        Vulkan::Vulkan
        glfw::glfw
        glm)