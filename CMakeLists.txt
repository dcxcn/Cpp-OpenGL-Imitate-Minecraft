cmake_minimum_required(VERSION 3.0)
project(NextCraft)
find_package(glfw3 CONFIG REQUIRED)
find_package(png REQUIRED)
add_definitions(${PNG_DEFINITIONS})
find_package(freetype REQUIRED)
include_directories(./src ./include ${GLFW3_INCLUDE_DIRS} ${PNG_INCLUDE_DIRS} ${FREETYPE_INCLUDE_DIRS})
install(DIRECTORY "${CMAKE_SOURCE_DIR}/deps/" DESTINATION "${CMAKE_BINARY_DIR}/")
FILE(GLOB SOURCE_FILES src/*.cpp)
add_executable(NextCraft ${SOURCE_FILES} ./include/glad.c)
target_link_libraries(NextCraft PRIVATE ${FREETYPE_LIBRARIES} glfw3 ${PNG_LIBRARIES})