cmake_minimum_required(VERSION 3.5)
project(cpp-rpg)

option(ENABLE_COVERAGE "Enable coverage" FALSE)

if (ENABLE_COVERAGE)
  add_compile_options(--coverage -O0)
endif()

if (MSVC)
  add_compile_options(/W4)
else()
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

add_executable(cpp-rpg "src/main.cpp")
target_link_libraries(cpp-rpg --coverage)

enable_testing()

add_executable(tester "test/tester.cpp")
target_link_libraries(tester --coverage)
add_test(Tester tester)