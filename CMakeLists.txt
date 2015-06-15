cmake_minimum_required(VERSION 2.7)
project(lod)

set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/lib)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_SOURCE_DIR}/bin)



find_package(GLUT REQUIRED)
include_directories(${GLUT_INCLUDE_DIRS})
link_directories(${GLUT_LIBRARY_DIRS})
add_definitions(${GLUT_DEFINITIONS})

find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIRS})
link_directories(${OpenGL_LIBRARY_DIRS})
add_definitions(${OpenGL_DEFINITIONS})

add_executable(lod main.c aabb.c draw_string.c mesh.c octree.c shader.c timer.c view_params.c vfc.c)

target_link_libraries(lod ${OPENGL_LIBRARIES} ${GLUT_LIBRARY} m)

add_custom_target(copy_bunny)
add_custom_command(TARGET copy_bunny PRE_BUILD
                     COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_CURRENT_SOURCE_DIR}/bunny.ply ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/bunny.ply)
add_dependencies(lod copy_bunny)

add_custom_target(copy_shaders)
set(SHADER_FILES shader.frag simple-shader.frag shader.vert simple-shader.vert)
foreach(ShaderFile ${SHADER_FILES})
  add_custom_command(TARGET copy_shaders PRE_BUILD
                     COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_CURRENT_SOURCE_DIR}/${ShaderFile} ${CMAKE_RUNTIME_OUTPUT_DIRECTORY}/${ShaderFile})
endforeach()
add_dependencies(lod copy_shaders)

