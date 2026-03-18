cmake_minimum_required(VERSION 3.20)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -I${CMAKE_CURRENT_LIST_DIR}/../../zmk/app/include")

zephyr_library()
zephyr_library_sources_ifdef(CONFIG_ZMK_SPLIT_ROLE_CENTRAL
    src/led_status_central.c)
zephyr_library_sources_ifdef(CONFIG_ZMK_SPLIT_ROLE_PERIPHERAL
    src/led_status_peripheral.c)
