cmake_minimum_required(VERSION 2.8)

project(Sotumerp)

include_directories(${CMAKE_SOURCE_DIR}/src)

################################################################################
# system specifics

set(CMAKE_CXX_FLAGS "-O0 -ggdb --std=c++11")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} --coverage")

################################################################################
# sotumerp
add_executable(sotumerp src/sotumerp.cpp)

################################################################################
# coverage
set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/CMakeModules)
if(CMAKE_COMPILER_IS_GNUCXX)
    include(CodeCoverage)
    setup_target_for_coverage(sotumerp-cov folk folk-coverage)
endif()

################################################################################
# install
install(TARGETS sotumerp RUNTIME DESTINATION bin)
