# games

Games in **all deployable forms** — the same puzzles (sudoku · logic-grid · crosswords) rendered per platform. No backend, no database, no accounts.

## 🚀 Deployables

| Folder | Platform | Renderer |
| --- | --- | --- |
| [`browser/`](browser) | web (GitHub Pages) | Rust + WebAssembly |
| [`windows/`](windows) | native Windows | Godot |
| [`unix/`](unix) | native Linux / macOS | Godot |

The folder names are **platforms**; the engine is an implementation detail.

## 🧩 Shared

- [`catalog/`](catalog) — `games.yaml` (the source of truth) + tags.
- [`data/`](data) — per-game puzzle banks.
- [`assets/`](assets) — submodule ([`kapetim/assets`](https://github.com/kapetim/assets)): images · fonts · audio, shared with the other deployables and `data-science`.

## 🗂️ Structure

```text
catalog/            games.yaml + tags
data/               per-game static datasets
browser/            web deployable
  rust/             Rust workspace (wasm32 engines)
  frontend/         React + TS launcher
windows/            native Windows deployable (Godot)
unix/               native Unix deployable (Godot)
assets/             shared assets submodule
docs/               GAMES / GOALS / REQUIREMENTS
```

## 🎮 Games

The catalog ([`catalog/games.yaml`](catalog/games.yaml)) is the source of truth — the three pillars, each mapped to a `/play/<slug>` route:

| Game | Route |
| --- | --- |
| Sudoku | `/play/sudoku` |
| Logic Grid | `/play/logic-puzzles` |
| Crosswords | `/play/crosswords` |

Other game ideas live as issues — see [`docs/GAMES.md`](docs/GAMES.md). Add-a-game boilerplate: [`docs/ADD-A-GAME.md`](docs/ADD-A-GAME.md).

## ⚡ Quick start

```bash
# assets (submodule)
git submodule update --init --recursive

# browser deployable
npm --prefix browser/frontend/launcher run dev
cargo build --workspace -p sudoku -p logic-grid -p crosswords
```

## 📄 Docs

- [`docs/GAMES.md`](docs/GAMES.md) — game issue roadmap
- [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md) — game requirements
- [`docs/GOALS.md`](docs/GOALS.md) — project goals
