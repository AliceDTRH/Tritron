cmake_minimum_required(VERSION 3.23)

project(Tritron)

add_library(tritlib)

target_sources(tritlib PRIVATE src/tritlib/trit.c
  PRIVATE src/tritlib/strtrit.c
  PUBLIC FILE_SET HEADERS
  BASE_DIRS 
    src/tritlib
  FILES
    src/tritlib/trit.h
    src/tritlib/strtrit.h 
    src/tritlib/trit128.h
)
add_executable(tritron)
target_sources(tritron PRIVATE src/tritron.c)


find_library(MATH_LIBRARY m)
if(MATH_LIBRARY)
    target_link_libraries(tritlib PUBLIC ${MATH_LIBRARY})
endif()


target_link_libraries(tritron tritlib)


Include(FetchContent)

FetchContent_Declare(
  Catch2
  GIT_REPOSITORY https://github.com/catchorg/Catch2.git
  GIT_TAG        v3.8.1 # or a later release
)

FetchContent_MakeAvailable(Catch2)

add_executable(tests test.cpp)
target_link_libraries(tests PRIVATE Catch2::Catch2WithMain)

