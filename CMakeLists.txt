# This probably doesn't comply with standards! Feel free to fix it.
set (CMAKE_CXX_STANDARD 11)
cmake_minimum_required(VERSION 3.1)
project(peripherycpp)
add_subdirectory(c-periphery)
message("Building peripherycpp")
file(GLOB_RECURSE ${PROJECT_NAME}_SOURCES src/*.cpp src/*.hpp)
add_library(${PROJECT_NAME} ${${PROJECT_NAME}_SOURCES})
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 11)
target_include_directories(${PROJECT_NAME} PUBLIC include)
target_link_libraries(${PROJECT_NAME} c-periphery)

#diag executables
if(ENABLE_DIAG)
    # Get test source files and doag data files
    file(GLOB_RECURSE ${PROJECT_NAME}_DIAG_SOURCES "diag/*.cpp")
    foreach(diagFile ${${PROJECT_NAME}_DIAG_SOURCES})
        get_filename_component(name ${diagFile} NAME_WE)
        message("Building diagnostic file: ${name}")
        add_executable(${name} ${diagFile})
        set_property(TARGET ${name} PROPERTY CXX_STANDARD 11)
        target_link_libraries(${name} ${PROJECT_NAME})
    endforeach()
endif()
