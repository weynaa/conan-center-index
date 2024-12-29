cmake_minimum_required(VERSION 3.15)
project(test_package LANGUAGES CXX)
find_package(STDEXEC REQUIRED)

add_executable(${PROJECT_NAME} test_package.cpp)
target_link_libraries(${PROJECT_NAME} PRIVATE STDEXEC::stdexec)

if(TARGET STDEXEC::system_context)
    target_link_libraries(${PROJECT_NAME} PRIVATE STDEXEC::system_context)
else()
    target_compile_definitions(${PROJECT_NAME} PRIVATE STDEXEC_SYSTEM_CONTEXT_HEADER_ONLY)
endif()
