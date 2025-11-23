add_executable(remotedesk_host
  main.c
  capture/capture_x11.c
  capture/capture_quartz.c
  encode/encode_png.c
  encode/encode_rle.c
  ../net/net_server.c
  ../utils/timer.c
  ../utils/log.c
)


#Linux Requirements
if(UNIX AND NOT APPLE)
  find_package(X11 REQUIRED)
  target_link_libraries(remotedesk_host X11)
endif()


#MacOS Requirements
if(APPLE)
  find_library(COCOA_LIB Cocoa)
  find_library(QUARTZ_LIB QuartzCore)
  target_link_libraries(remotedesk_host ${COCOA_LIB} ${QUARTZ_LIB})
endif()


find_package(PNG REQUIRED)
target_link_libraries(remotedesk_host PNG::PNG)
