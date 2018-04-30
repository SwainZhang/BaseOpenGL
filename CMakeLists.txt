cmake_minimum_required(VERSION 3.7)
project(testGL)

#add_definitions(${GCC_COVERAGE_COMPILE_FLAGS})
#find_package(OpenGL REQUIRED)
#find_package(glew REQUIRED)

set(CMAKE_CXX_STANDARD 11)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -v -stdlib=libc++")
#set(CMAKE_CXX_FLAGS "-framework OpenGL")

set(SOURCE_FILES main.cpp )
set(INCLUDE_DIR ./include)

set(LINK_INC_DIR /usr/local/include)
set(LINK_LIB_DIR /usr/local/lib)

SET(GCC_COVERAGE_LINK_FLAGS "-L/usr/local/lib -lglfw -lglew")
SET(CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${GCC_COVERAGE_LINK_FLAGS}")

include_directories(${INCLUDE_DIR})

#link_directories(${LINK_INC_DIR})
#link_libraries(${LINK_LIB_DIR})


add_executable(testGL ${SOURCE_FILES})

target_link_libraries(
        testGL
        # ${LINK_LIB_DIR}
)
target_include_directories(testGL PUBLIC ${OPENGL_INCLUDE_DIR})
target_link_libraries(testGL ${OPENGL_gl_LIBRARY})
target_link_libraries(testGL ${OPENGL_glu_LIBRARY})