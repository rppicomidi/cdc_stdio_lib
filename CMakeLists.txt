cmake_minimum_required(VERSION 3.13)

add_library(cdc_stdio_lib INTERFACE)
target_sources(cdc_stdio_lib INTERFACE
    ${CMAKE_CURRENT_LIST_DIR}/cdc_stdio_lib.c
)
target_include_directories(cdc_stdio_lib INTERFACE
 ${CMAKE_CURRENT_LIST_DIR}
)
target_link_libraries(cdc_stdio_lib INTERFACE pico_stdlib tinyusb_device)