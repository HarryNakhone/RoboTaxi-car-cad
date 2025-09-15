cmake_minimum_required(VERSION 3.13.1)

# list(APPEND ZEPHYR_EXTRA_MODULES 
#      ${CMAKE_CURRENT_LIST_DIR}/services/Motor_driver_service)

find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(pwm)

set(BOARD_FLASH_RUNNER stm32cubeprogrammer)

list(APPEND CMAKE_MODULE_PATH ${ZEPHYR_BASE}/modules/nanopb)
include(nanopb)

zephyr_nanopb_sources(app applications/proto/motor_uart.proto)

# target_include_directories(app PRIVATE ${CMAKE_CURRENT_LIST_DIR}/services/Motor_driver_service)

target_sources(app PRIVATE applications/sender_rc.c)
