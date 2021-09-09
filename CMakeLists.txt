ke_minimum_required(VERSION 3.13)

include(pico_sdk_import.cmake)

project(moter_control C CXX ASM)
set(CMAKE_C_STNDARD 11)
set(CMAKE_CXX_STANDARD 17)

pico_sdk_init()

add_executable(moter_control
        moter_control.c
)

# Pull in our pico_stdlib which pulls in commonly used features
target_link_libraries(moter_control pico_stdlib hardware_uart)

# enable usb output, disable uart output
pico_enable_stdio_usb(moter_control 1)
pico_enable_stdio_uart(moter_control 0)

# create map/bin/hex file etc.
pico_add_extra_outputs(moter_control)
