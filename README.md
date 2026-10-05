# NW.js runtime mirror for Brave Engine

Re-hosted copies of [NW.js](https://nwjs.io)'s own official binaries, pinned to the exact version Brave Engine's packaging depends on (`devDependencies.nw` in the main repo's `package.json`). Brave Engine's packaging pipeline (the editor's Build Project, the Hub and editor build scripts — all through [`nw-builder`](https://github.com/nwjs-community/nw-builder)) fetches from here instead of `dl.nwjs.io`/`nwjs.io` directly, so a build never depends on NW.js's own distribution infrastructure staying up or fast.

One release per NW.js version, and each tag is the literal NW.js version it mirrors (e.g. `v0.107.0`) — `nw-builder`'s own URL construction (`{downloadUrl}/v{version}/{file}`) requires that exact shape, not a free choice. Each release carries the binaries (win-x64, linux-x64, osx-arm64), `SHASUMS256.txt` (checked against NW.js's own official file before upload), and its `versions.json` lives on `main` at `v<version>/versions.json` (the version manifest `nw-builder` otherwise fetches from `nwjs.io`).

No source lives in this repository. It must stay **public** — GitHub release assets inherit the repository's visibility, with no per-release override, and both `nw-builder`'s own fetch and a user's own build need that.

Other Brave Engine downloads live in their own repositories: `brave-engine-releases` (the editor) and `brave-hub-releases` (the Hub).
