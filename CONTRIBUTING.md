# Contributing to Netrek COM

Thanks for helping make **Netrek Client of Mac (COM)** better. Whether you're
reporting a bug or sending a fix, this page tells you exactly how so it lands fast.

## "Hey, this doesn't work" — reporting a bug

The single most useful thing you can do is file a good bug report. Open one here:

**→ https://github.com/ElevateConsultingDev/netrek-clients/issues/new/choose**

A good report includes:

1. **What you did** — the steps, and what you were doing in-game.
2. **What you expected** vs **what actually happened**.
3. **Your setup** — macOS version, Apple Silicon or Intel, how you launched it, and the
   client version (shown on the team-select screen, e.g. `Netrek COM 0.9`).
4. **Your `~/.netrekrc`** (paste the relevant lines).
5. **Any output** — run from Terminal and copy the console text; for input issues, run with
   `NETREK_INPUT_DEBUG=1` and attach `/tmp/netrek-input.log`.
6. A **screenshot** if it's visual.

No detail is too small. "The phaser draws from the wrong spot when the window is maximized"
is a perfect report.

## Building for development

```sh
brew install sdl2 sdl2_image sdl2_ttf sdl2_mixer pkg-config
cd netrek-client-cow-sdl2
make            # -> build/netrek-sdl2
make clean      # if you change a shared header (the Makefile doesn't track header deps)
```

## Where the code lives

- **`netrek-client-cow-sdl2/`** — the COM-specific code. Almost all Mac/SDL2 work happens
  here: `sdl2window.c` (windowing, input, compositor), `sdl2sprite.c` (sprites), `sdl2camera.c`.
- **`netrek-client-cow/`** — upstream COW C sources that COM compiles against. Touch these
  only for genuinely shared logic (e.g. `map.c`, `input.c`); prefer keeping changes in the
  SDL2 layer.

## Sending a change (PR)

1. Fork, branch from `main`.
2. Keep the diff focused — one fix or feature per PR. Match the surrounding code style.
3. Build clean (`make`) and actually run it against a server before submitting.
4. **Sign off your commits** with the [Developer Certificate of Origin](https://developercertificate.org/):
   ```sh
   git commit -s -m "your message"
   ```
   The `-s` adds a `Signed-off-by:` line certifying you wrote the code and can contribute it
   under the project's license.
5. Open the PR describing what changed and how you tested it.

## License of contributions

Netrek COM is **GPLv2-or-later** (see `LICENSE`). By contributing you agree your
contribution is licensed under those same terms. Original COW/Netrek code remains under its
original authors' copyright; new Mac/SDL2 work is © Dave King / Elevate Consulting.

## Maintainer

Dave King · dave@elevateconsulting.dev — the canonical home for Netrek COM is
[ElevateConsultingDev/netrek-clients](https://github.com/ElevateConsultingDev/netrek-clients).
