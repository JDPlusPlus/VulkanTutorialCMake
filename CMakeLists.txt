cmake_minimum_required(VERSION 3.0) # You can change this if you wish
project(VulkanTutorialCMake)

set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/modules/)
link_directories(${CMAKE_SOURCE_DIR}/lib)

find_package(glfw3 REQUIRED)
message(STATUS "Found GLFW3 in ${GLFW3_INCLUDE_DIR}")
find_package(glm REQUIRED)
find_package(Vulkan REQUIRED)
set(SOURCE_FILES src/main.cpp)

add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} PRIVATE
        Vulkan::Vulkan
        glfw
        glm
        )