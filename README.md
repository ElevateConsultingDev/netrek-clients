# Netrek SDL2 0.9

A native, retina-crisp **SDL2** Netrek client for macOS — a modernized port of
the classic COW ("Client Of Win") client. Vector graphics and text render at
full HiDPI, the window scales/letterboxes cleanly, and ship art is upgraded.

Landing page / server info: **https://netrek.elevateconsulting.dev**

## Build (macOS)

```sh
brew install sdl2 sdl2_image sdl2_ttf sdl2_mixer pkg-config
cd netrek-client-cow-sdl2
make
```

Produces `netrek-client-cow-sdl2/build/netrek-sdl2`.

## Run

```sh
./build/netrek-sdl2 -h sturgeon.elevateconsulting.dev -p 2592
```

The `sturgeon.elevateconsulting.dev` server is **IP-restricted** — email
**dave@elevateconsulting.dev** with your public IP to be whitelisted. You can
also point `-h` at any public Netrek server.

Recommended `~/.netrekrc`: `tryShort: off`.

## Layout

- `netrek-client-cow-sdl2/` — the SDL2 backend + build (our work)
- `netrek-client-cow/` — upstream COW sources it compiles against

## Credits

Based on netrek-client-cow by the Netrek community (https://www.netrek.org/).
Netrek is free and open source.
