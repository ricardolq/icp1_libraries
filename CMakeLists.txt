cmake_minimum_required(VERSION 3.10)

project(mymath LANGUAGES C)

add_library(mymath STATIC src/mymath.c)

target_include_directories(mymath PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
)

install(TARGETS mymath
        EXPORT mymathTargets
        ARCHIVE DESTINATION lib
        RUNTIME DESTINATION bin)

install(EXPORT mymathTargets
        FILE mymathConfig.cmake
        DESTINATION cmake)

install(DIRECTORY include/ DESTINATION include)
