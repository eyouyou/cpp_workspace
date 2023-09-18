cmake_minimum_required (VERSION 3.8)

project ("XXX.Test")

find_package(GTest CONFIG REQUIRED)

add_executable(${PROJECT_NAME} tmain.cpp)

target_link_libraries(${PROJECT_NAME} PRIVATE GTest::gtest)

include(GoogleTest)
gtest_add_tests(TARGET ${PROJECT_NAME})