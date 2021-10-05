cmake_minimum_required(VERSION 3.5)
project(cpp-rpg)

if (MSVC)
  add_compile_options(/W4)
else()
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

add_executable(cpp-rpg "src/main.cpp" "test/tester.cpp")
target_compile_features(cpp-rpg PRIVATE cxx_lambda_init_captures)

enable_testing()

add_executable(tester "test/tester.cpp")
add_test(Tester tester)