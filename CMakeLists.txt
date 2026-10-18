cmake_minimum_required(VERSION 3.20)

project(dynamic-replica)

# Geode 5 requiere C++23
set(CMAKE_CXX_STANDARD 23)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# 1. Carga el SDK de Geode.
# La variable de entorno GEODE_SDK debe apuntar a tu instalación de Geode.
add_subdirectory($ENV{GEODE_SDK} ${CMAKE_CURRENT_BINARY_DIR}/geode)

add_library(${PROJECT_NAME} SHARED
    src/main.cpp
)

# 2. Ahora setup_geode_mod ya está definida y puede configurar el mod.
setup_geode_mod(${PROJECT_NAME})