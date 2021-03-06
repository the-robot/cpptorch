cmake_minimum_required(VERSION 3.17)
project(cpptorch)

set(CMAKE_CXX_STANDARD 14)
set(CMAKE_PREFIX_PATH <PATH_TO_YOUR_LIBTORCH_LIBRARY>)

find_package(Torch REQUIRED)

add_executable(cpptorch main.cpp)
target_link_libraries(cpptorch "${TORCH_LIBRARIES}")
set_property(TARGET cpptorch PROPERTY CXX_STANDARD 14)

# The following code block is suggested to be used on Windows.
# According to https://github.com/pytorch/pytorch/issues/25457,
# the DLLs need to be copied to avoid memory errors.
if (MSVC)
    file(GLOB TORCH_DLLS "${TORCH_INSTALL_PREFIX}/lib/*.dll")
    add_custom_command(TARGET cpptorch
            POST_BUILD
            COMMAND ${CMAKE_COMMAND} -E copy_if_different
            ${TORCH_DLLS}
            $<TARGET_FILE_DIR:cpptorch>)
endif (MSVC)
