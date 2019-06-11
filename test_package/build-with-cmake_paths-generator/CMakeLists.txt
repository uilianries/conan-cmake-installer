project(test_package_cmake_paths)
cmake_minimum_required(VERSION 2.8.11)

include(${CMAKE_BINARY_DIR}/conan_paths.cmake)

find_package(PahoMqttCpp REQUIRED)
find_package(Threads REQUIRED)

add_executable(${PROJECT_NAME} ${CMAKE_SOURCE_DIR}/test_package.cpp)
set_target_properties(${PROJECT_NAME} PROPERTIES OUTPUT_NAME test_package)
set_target_properties(${PROJECT_NAME} PROPERTIES CXX_STANDARD 11)
if(PAHO_BUILD_STATIC)
	target_link_libraries(${PROJECT_NAME} PahoMqttCpp::paho-mqttpp3-static)
else()
	target_link_libraries(${PROJECT_NAME} PahoMqttCpp::paho-mqttpp3)
endif()
target_link_libraries(${PROJECT_NAME} Threads::Threads)
