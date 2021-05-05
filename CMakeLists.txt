cmake_minimum_required(VERSION 3.14)
project(aprendiendo VERSION 0.1.0)

include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

add_subdirectory(googletest) # add googletest subdirectory

include_directories(googletest/include) # this is so we can #include <gtest/gtest.h>

# Now simply link against gtest or gtest_main as needed.

add_executable(testprimer helloworld.cpp) # add this executable

target_link_libraries(testprimer PRIVATE gtest) # link google test to this executable

add_executable(mistests functests_unittest.cc functests.cpp)

target_link_libraries(mistests PRIVATE gtest) # link google test to this executable
target_link_libraries(mistests PRIVATE gtest_main) # link google test to this executable