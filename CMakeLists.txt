cmake_minimum_required(VERSION 3.10)
project(gazebo_dart_vendor)

find_package(ament_cmake REQUIRED)
find_package(ament_cmake_vendor_package REQUIRED)

ament_vendor(${PROJECT_NAME}
  VCS_URL https://github.com/dartsim/dart.git
  VCS_VERSION v6.13.1
  CMAKE_ARGS
    -DDART_BUILD_OSG:BOOL=FALSE
    -DDART_BUILD_GUI_OSG:BOOL=FALSE
    -DDART_BUILD_DARTPY:BOOL=FALSE
    -DDART_TREAT_WARNINGS_AS_ERRORS:BOOL=FALSE # TODO(azeey) Remove when https://github.com/dartsim/dart/issues/1781 is resolved.
  GLOBAL_HOOK
)

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
