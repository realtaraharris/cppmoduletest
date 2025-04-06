cmake_minimum_required(VERSION 3.31)

project(CppModuleTest)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

add_executable(my_app main.cpp)

target_sources(
  my_app
  PRIVATE FILE_SET CXX_MODULES FILES my_module.cppm # Interface unit first
  PRIVATE my_module.cpp # Implementation next
)

target_compile_options(my_app PRIVATE -std=c++20 -fmodules)
