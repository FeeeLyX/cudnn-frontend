cmake_minimum_required(VERSION 3.16)

project(cudnn_frontend VERSION 0.9)

set(CUDA_TOOLKIT_ROOT_DIR "/usr/local/cuda")

option(CUDNN_FRONTEND_BUILD_SAMPLES "Defines if samples are built or not." ON)

add_library(cudnn_frontend INTERFACE)

target_include_directories(
    cudnn_frontend INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

target_compile_features(cudnn_frontend INTERFACE cxx_std_11)

if (${CUDNN_FRONTEND_BUILD_SAMPLES})
add_subdirectory(samples)
endif()
