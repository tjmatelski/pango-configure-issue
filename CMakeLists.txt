cmake_minimum_required(VERSION 3.0)
project(pango-configure-issue)

# Find all pkgconfig directories for vcpkg installed libraries
file(GLOB VCPKG_PKG_CONFIG_DIRS LIST_DIRECTORIES true ${CMAKE_SOURCE_DIR}/extern/vcpkg/packages/*/lib/pkgconfig/)
list(JOIN VCPKG_PKG_CONFIG_DIRS ":" VCPKG_PKG_CONFIG_DIRS)
find_package(PkgConfig REQUIRED)
set(ENV{PKG_CONFIG_PATH} $ENV{PKG_CONFIG_PATH}":"${VCPKG_PKG_CONFIG_DIRS})

# Use pkg-config to generate CMake target of pango
pkg_check_modules(PANGO_LIB REQUIRED IMPORTED_TARGET pango)

add_executable(hello main.cpp)
target_link_libraries(hello PRIVATE PkgConfig::PANGO_LIB)