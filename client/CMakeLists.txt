add_executable(remotedesk_client
  main.c
  render/render_sdl.c
  ../net/net_client.c
  ../utils/timer.c
)


find_package(SDL2 REQUIRED)
target_link_libraries(remotedesk_client SDL2::SDL2)
