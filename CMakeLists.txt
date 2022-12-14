# Generated Cmake Pico project file

cmake_minimum_required(VERSION 3.13)

set(CMAKE_C_STANDARD 11)
set(CMAKE_CXX_STANDARD 17)

# Initialise pico_sdk from installed location
# (note this can come from environment, CMake cache etc)
set(PICO_SDK_PATH "C:/Users/j_gab/Documents/Pico/pico-sdk")

# Pull in Raspberry Pi Pico SDK (must be before project)
include(pico_sdk_import.cmake)

project(telemetria_tx C CXX ASM)

# Initialise the Raspberry Pi Pico SDK
pico_sdk_init()

# Add executable. Default name is the project name, version 0.1

add_executable(telemetria_tx telemetria_tx.c mpu9250.c)

add_subdirectory(lib/pico-nrf24/lib/nrf24l01)

pico_set_program_name(telemetria_tx "telemetria_tx")
pico_set_program_version(telemetria_tx "0.1")

pico_enable_stdio_uart(telemetria_tx 0)
pico_enable_stdio_usb(telemetria_tx 1)

# Add the standard library to the build
target_link_libraries(telemetria_tx pico_stdlib nrf24_driver)

pico_add_extra_outputs(telemetria_tx)

