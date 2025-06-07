cmake_minimum_required(VERSION 3.10)
project(Cube3D)

set(CMAKE_CXX_STANDARD 17)

# Inclui headers locais (ex: para glad e glm)
include_directories(include)

# Encontra GLFW via pkg-config
find_package(PkgConfig REQUIRED)
pkg_check_modules(GLFW REQUIRED glfw3)

# Adiciona executável e fontes
add_executable(Cube3D 
    src/main.cpp 
    src/gl.c           # glad core profile gerado
)

# Inclui diretórios (GLFW + headers locais + GLM)
target_include_directories(Cube3D PRIVATE 
    ${GLFW_INCLUDE_DIRS}
    include           # para glad e glm headers
)

# Linka bibliotecas GLFW, dl (Linux), m (math)
target_link_libraries(Cube3D
    ${GLFW_LIBRARIES}
    dl
    m
)
