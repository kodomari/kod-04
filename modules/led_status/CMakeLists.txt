cmake_minimum_required(VERSION 3.20)

add_library(led_status STATIC "")
set_property(GLOBAL APPEND PROPERTY ZEPHYR_LIBS led_status)

set(ZMK_INC "-I${CMAKE_CURRENT_LIST_DIR}/../../zmk/app/include")

if(CONFIG_ZMK_SPLIT_ROLE_CENTRAL)
    set(src ${CMAKE_CURRENT_LIST_DIR}/src/led_status_central.c)
    target_sources(led_status PRIVATE ${src})
    set_source_files_properties(${src} PROPERTIES COMPILE_OPTIONS ${ZMK_INC})
elseif(CONFIG_ZMK_SPLIT_ROLE_PERIPHERAL)
    set(src ${CMAKE_CURRENT_LIST_DIR}/src/led_status_peripheral.c)
    target_sources(led_status PRIVATE ${src})
    set_source_files_properties(${src} PROPERTIES COMPILE_OPTIONS ${ZMK_INC})
endif()
