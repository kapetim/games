# browser-games

Front-end only browser games with a Rust + WASM focus — like the puzzle rack at a newsstand, but ephemeral. The **launcher** is the home page: one game selector that drops you into any game. No backend, no database, no accounts — state lives in the browser and disappears when you close the tab. Rust-first, no TypeScript outside the launcher.

## Focus

Three daily pillars:

- **Sudoku** — generator + auto-solve.
- **Logic grid** — grid deduction with green-check marking (the phrases game).
- **Crosswords** — solver-first with a curated puzzle bank.

Other game ideas live as issues, not in the active catalog. See [docs/ADD-A-GAME.md](docs/ADD-A-GAME.md) for the add-a-game boilerplate.

## Structure

```text
src/
  rust/            Rust workspace
    engines/       wasm32 crates (single-threaded, canvas) — sudoku · logic-grid · crosswords
  frontend/
    launcher/      React + TS (the only TS UI) — game selector
  catalog/         games.yaml (the roadmap) + tags
  data/            per-game static datasets
docs/              GAMES / GOALS / REQUIREMENTS
```

## Games

The catalog (`src/catalog/games.yaml`) is the source of truth — the active games are the three pillars, each mapped to a `/play/<slug>` route:

| Game | Route |
|---|---|
| Sudoku | `/play/sudoku` |
| Logic Grid | `/play/logic-puzzles` |
| Crosswords | `/play/crosswords` |

Other game ideas (n-queens, numerox, tango, chess, checkers, nonogram, and others) are tracked as issues — see `docs/GAMES.md`.

## Quick start

```bash
npm --prefix src/frontend/launcher run dev
cargo build --workspace -p sudoku -p logic-grid -p crosswords
```

Deployed as a static site on GitHub Pages.

## Docs

- [`docs/GAMES.md`](docs/GAMES.md) — game issue roadmap
- [`docs/REQUIREMENTS.md`](docs/REQUIREMENTS.md) — game requirements
- [`docs/GOALS.md`](docs/GOALS.md) — project goals
