# This probably doesn't comply with standards! Feel free to fix it.
cmake_minimum_required(VERSION 3.1)
project(peripherycpp)

file(GLOB_RECURSE ${PROJECT_NAME}_SOURCES src/*.cpp src/*.hpp)
add_library(${PROJECT_NAME} ${${PROJECT_NAME}_SOURCES})
set_property(TARGET ${PROJECT_NAME} PROPERTY CXX_STANDARD 11)
target_include_directories(${PROJECT_NAME} PUBLIC include)
target_link_libraries(${PROJECT_NAME} periphery)

#diag executables
if(ENABLE_DIAG)
    # Get test source files and doag data files
    # todo: remove file extension from filenames
    file(GLOB_RECURSE ${PROJECT_NAME}_DIAG_SOURCES "diag/*.cpp")
    foreach(diagFile ${${PROJECT_NAME}_DIAG_SOURCES})
        file(RELATIVE_PATH name ${CMAKE_CURRENT_SOURCE_DIR}/diag ${diagFile})
        string(SUBSTRING name 0 (LENGTH name -4) name)
        add_executable(${name} ${diagFile})
        set_property(TARGET ${name} PROPERTY CXX_STANDARD 11)
        target_link_libraries(${name} ${PROJECT_NAME})
    endforeach()
endif()

endif()
