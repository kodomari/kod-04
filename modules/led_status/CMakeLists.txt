cmake_minimum_required(VERSION 3.20)

set(lib_name led_status)
zephyr_library_named(${lib_name})
target_include_directories(${lib_name} PRIVATE
    ${CMAKE_CURRENT_LIST_DIR}/../../zmk/app/include)
zephyr_library_sources_ifdef(CONFIG_ZMK_SPLIT_ROLE_CENTRAL
    src/led_status_central.c)
zephyr_library_sources_ifdef(CONFIG_ZMK_SPLIT_ROLE_PERIPHERAL
    src/led_status_peripheral.c)
