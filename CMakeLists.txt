cmake_minimum_required(VERSION 3.25.2)
project(wxWidgets_canvas_test)
set(CMAKE_CXX_STANDARD 20)

include(ConfigFunctions.cmake)


# DIRECTORIES
set_project_directories(src src test res include lib out)


# EXECUTABLE
set(EXECUTABLE_NAME ${CMAKE_PROJECT_NAME})
add_executable(${EXECUTABLE_NAME} ${HEADER_FILES} ${SOURCE_FILES})


# LIBRARIES

#find_package(wxWidgets QUIET REQUIRED)
#include(${wxWidgets_USE_FILE})
#target_link_libraries(${EXECUTABLE_NAME} PRIVATE ${wxWidgets_LIBRARIES})

find_package(wxWidgets QUIET REQUIRED COMPONENTS all)
include(${wxWidgets_USE_FILE})
target_link_libraries(${EXECUTABLE_NAME} PRIVATE ${wxWidgets_LIBRARIES})

find_libraries(LIBRARIES REQUIRED OpenGL gl GLU glut)
target_link_libraries(${EXECUTABLE_NAME} PRIVATE ${LIBRARIES})


#execute_process(COMMAND wx-config --libs --cxxflags --gl-libs OUTPUT_VARIABLE WX_CONFIG_OUTPUT)
#message("${WX_CONFIG_OUTPUT}")
##add_compile_options(${WX_CONFIG_OUTPUT})
##add_link_options(${WX_CONFIG_OUTPUT})
#target_link_libraries(${EXECUTABLE_NAME} PRIVATE ${WX_CONFIG_OUTPUT})