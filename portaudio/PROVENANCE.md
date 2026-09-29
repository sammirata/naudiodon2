# PortAudio binaries

Every file in `bin/` is built by CI from
https://github.com/sammirata/portaudio at tag `pa-v19.7.0-sr1`, which is
upstream PortAudio `v19.7.0` plus a `ci/` directory and a workflow - no
PortAudio source file is modified (`git diff v19.7.0..pa-v19.7.0-sr1`
touches only `ci/` and `.github/`). Build recipes: `ci/README.md` there.

| file                 | sha256                                                             |
| -------------------- | ------------------------------------------------------------------ |
| `libportaudio.dylib` | `64c3ca3a09a03215794f227624278485abcc1d9e0233669e9d82b282869e94fe` |
| `libportaudio.so.2`  | `c24a2f3e672c15db042be646dc61b96958893142fbc6e06e6ff17ead7fb5da23` |
| `portaudio_x64.dll`  | `f63a8a0c903b60d065c60aaeb9f904c72b02e5cffa3040643c1bd18987c0b887` |
| `portaudio_x64.lib`  | `e41a5e125cbde3facfd5ea3cc6df3a78bd83923035d242b510b932c55bf7cf37` |

The hashes are those of the assets on the `pa-v19.7.0-sr1` GitHub release.
MSVC stamps a timestamp and PDB GUID into every build, so a rebuild of the
DLL differs from these bytes in those fields only.

`include/` is byte-identical to `include/` at upstream `v19.7.0`.

Only win32-x64, darwin (x86_64 + arm64) and linux-x64 are built; there is
no 32-bit ARM Linux library.
