cmake_minimum_required(VERSION 4.0)
project(test)
set(CMAKE_CXX_STANDARD 17)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

aux_source_directory(${PROJECT_SOURCE_DIR}/src SRC_LISTS)
add_library(common
SHARED
${SRC_LISTS}
)

target_include_directories(common
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

add_executable(test main.cpp)

target_include_directories(test
PUBLIC
${PROJECT_SOURCE_DIR}/include
)

target_link_libraries(test
PUBLIC
common
)