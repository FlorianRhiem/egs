cmake_minimum_required(VERSION 3.1.3 FATAL_ERROR)

project(egs VERSION 0.0.1)

SET(CMAKE_INSTALL_RPATH "@loader_path/../../../lib/egs")
add_executable(molecule_example_c molecule_example.c)
target_link_libraries(molecule_example_c ${PROJECT_NAME} util)
target_include_directories(molecule_example_c PRIVATE ${PROJECT_SOURCE_DIR}/../egs/core ${PROJECT_SOURCE_DIR}/../egs/plugins/molecule_plugin)
install(TARGETS molecule_example_c DESTINATION egs/bin/examples)

add_executable(molecule_example_cxx molecule_example.cxx)
target_link_libraries(molecule_example_cxx ${PROJECT_NAME} util)
target_include_directories(molecule_example_cxx PRIVATE ${PROJECT_SOURCE_DIR}/../egs/core ${PROJECT_SOURCE_DIR}/../egs/plugins/molecule_plugin)
set_property(TARGET molecule_example_cxx PROPERTY CXX_STANDARD 11)
install(TARGETS molecule_example_cxx DESTINATION egs/bin/examples)

install(FILES molecule_example.py DESTINATION egs/bin/examples)
install(FILES h2o.xyz DESTINATION egs/bin/examples)
