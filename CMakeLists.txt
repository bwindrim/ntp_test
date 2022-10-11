cmake_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(test_project C CXX ASM)
set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)
pico_sdk_init()

add_executable(ntp_test
picow_ntp_client.c
)

pico_enable_stdio_usb(ntp_test 1)
pico_enable_stdio_uart(ntp_test 1)
pico_add_extra_outputs(ntp_test)

target_include_directories(ntp_test PRIVATE ${CMAKE_CURRENT_LIST_DIR} )

target_link_libraries(ntp_test pico_cyw43_arch_lwip_threadsafe_background pico_stdlib hardware_rtc)
