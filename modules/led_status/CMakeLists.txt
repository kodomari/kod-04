cmake_minimum_required(VERSION 3.20)

zephyr_library()
zephyr_include_directories(${CMAKE_SOURCE_DIR}/include)
zephyr_library_sources_ifdef(CONFIG_ZMK_SPLIT_ROLE_CENTRAL
    src/led_status_central.c)
zephyr_library_sources_ifdef(CONFIG_ZMK_SPLIT_ROLE_PERIPHERAL
    src/led_status_peripheral.c)
