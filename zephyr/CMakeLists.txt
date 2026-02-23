zephyr_library()

# CONFIGで有効になったときだけビルド
zephyr_library_sources_ifdef(CONFIG_KB_ZMK_PS2_MOUSE_TRACKPOINT_DRIVER
  ../drivers/ps2/ps2.c
  ../drivers/trackpoint/trackpoint.c
)
