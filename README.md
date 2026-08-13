# Netrek COM — Netrek Client of Mac

**Netrek COM** (*Client Of Mac*) is a native, retina-crisp **SDL2** Netrek client for
macOS — a modernized fork of the classic **COW** (*Client Of Win*). Where COW is the
long-standing Windows/X11 client, COM is the Mac counterpart: same battle-tested
netrek core, a new SDL2 rendering + input backend, and a look that's sharp on a
Retina display.

**Play / server info:** https://netrek.elevateconsulting.dev

This repo is the home of Netrek COM. It also carries the upstream COW sources it
builds against, so it compiles standalone.

---

## What's different from COW

- **Native SDL2 backend** (`sdl2window.c` / `sdl2sprite.c` / `sdl2camera.c`) replacing
  the X11/Imlib2 code — no XQuartz required.
- **Retina 2× supersampled rendering** — crisp text and vectors instead of an upscaled
  1× buffer.
- **Window scaling / fullscreen** with correct aim at any size (uniform letterbox; mouse
  and render share one transform).
- **Hi-res ship art** downscaled to the canonical size for a cleaner look.
- Quality-of-life config ported from netrekxp: **agriCAPS** (uppercase AGRI planet names),
  **showArmy** (army counts on the map), a cleaner galactic army icon, and more — see the
  [`.netrekrc` guide](https://netrek.elevateconsulting.dev/netrekrc.html).

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
**dave@elevateconsulting.dev** with your public IP to be whitelisted. You can also point
`-h` at any public Netrek server (see https://www.netrek.org/).

Recommended `~/.netrekrc`: `tryShort: off` — full config guide at
https://netrek.elevateconsulting.dev/netrekrc.html.

## Repo layout

| Path | What |
|------|------|
| `netrek-client-cow-sdl2/` | The SDL2 backend + Makefile — **the COM-specific code** |
| `netrek-client-cow/` | Upstream COW sources COM compiles against |
| `docs/` | The landing site (GitHub Pages → netrek.elevateconsulting.dev) |

## Something not working? Tell us

Bug reports and PRs are welcome — that's how COM gets better. Please
[open an issue](https://github.com/ElevateConsultingDev/netrek-clients/issues/new/choose)
and include your macOS version, how you built it, your `.netrekrc`, what you expected, and
what actually happened. See [CONTRIBUTING.md](CONTRIBUTING.md) for the details.

## Copyright & license

Netrek COM is **free software under the GNU General Public License, version 2 or later**
(see [LICENSE](LICENSE)) — the same copyleft as the COW code it builds on.

- The SDL2 backend and Mac-specific code (`sdl2*.c/.h` and related changes) are
  **© 2026 Dave King / Elevate Consulting**.
- The underlying COW / Netrek sources remain **© their original authors** (Chris Guthrie,
  Kevin P. Smith, Scott Silvey, Kurt Siegl, and many others — see `netrek-client-cow/COPYING`).

Because it's GPL, you're free to use, study, modify, and redistribute it. Contributions are
accepted under the same license (see CONTRIBUTING.md).

*Netrek COM is a community client for the free, open-source game **Netrek** (https://www.netrek.org/).*
