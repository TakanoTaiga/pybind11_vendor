cmake_minimum_required(VERSION 3.10)
project(pybind11_vendor CXX)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

find_package(pybind11 QUIET)

ament_vendor(pybind11_vendor
  SATISFIED ${pybind11_FOUND}
  VCS_URL https://github.com/pybind/pybind11.git
  VCS_VERSION ffa346860b306c9bbfb341aed9c14c067751feb8
  PATCHES
    pybind11-2.9.1-fix-windows-debug.patch
    pybind11-python-3.11.patch
  CMAKE_ARGS
    -DPYBIND11_TEST=OFF
  GLOBAL_HOOK
)

ament_package(CONFIG_EXTRAS_POST "${PROJECT_NAME}-extras.cmake")
