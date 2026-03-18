cmake_minimum_required(VERSION 3.20)

if(CONFIG_ZMK_SPLIT_ROLE_CENTRAL)
    target_sources(app PRIVATE src/led_status_central.c)
elseif(CONFIG_ZMK_SPLIT_ROLE_PERIPHERAL)
    target_sources(app PRIVATE src/led_status_peripheral.c)
endif()
