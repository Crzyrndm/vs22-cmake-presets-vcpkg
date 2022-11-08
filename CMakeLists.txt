cmake_minimum_required(VERSION 3.16.3)

project(lib-minimal CXX)
add_library(lib-minimal)

target_sources(lib-minimal
    PUBLIC
        include/lib-minimal.hpp
    PRIVATE
        src/lib-minimal.cpp
)

target_compile_features(lib-minimal
    PUBLIC
        cxx_std_20
)

target_include_directories(lib-minimal
    PUBLIC
        include
    PRIVATE
        src
)

find_package(gsl-lite CONFIG REQUIRED)
find_package(expected-lite CONFIG REQUIRED)

target_link_libraries(lib-minimal
    PUBLIC
        gsl::gsl-lite-v1
        nonstd::expected-lite
)
