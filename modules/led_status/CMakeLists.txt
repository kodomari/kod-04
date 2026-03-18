cmake_minimum_required(VERSION 3.20)

add_library(led_status STATIC "")
set_property(GLOBAL APPEND PROPERTY ZEPHYR_LIBS led_status)
target_include_directories(led_status PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/../../zmk/app/include)

if(CONFIG_ZMK_SPLIT_ROLE_CENTRAL)
    target_sources(led_status PRIVATE src/led_status_central.c)
elseif(CONFIG_ZMK_SPLIT_ROLE_PERIPHERAL)
    target_sources(led_status PRIVATE src/led_status_peripheral.c)
endif()
