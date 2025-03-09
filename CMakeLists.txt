cmake_minimum_required(VERSION 3.10) # You can change this if you wish
project(VulkanTutorialCMake)

set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/modules/)
link_directories(${CMAKE_SOURCE_DIR}/lib)

find_package(GLFW3 REQUIRED)
message(STATUS "Found GLFW3 in ${GLFW3_INCLUDE_DIR}")
message(STATUS "Found GLFW3 in ${GLFW3_LIBRARY}")
find_package(GLM REQUIRED)
message(STATUS "Found GLM in ${GLM_INCLUDE_DIR}")
find_package(Vulkan REQUIRED)
set(SOURCE_FILES src/main.cpp)
if(MSVC)
        target_link_options(${PROJECT_NAME} PUBLIC /ignore:4098) # Ignores the "NODEFAULTLIB" warning
endif(MSVC)
add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} PRIVATE
        Vulkan::Vulkan
        ${GLFW3_LIBRARY}
        )
target_include_directories(${PROJECT_NAME} PRIVATE includes)
