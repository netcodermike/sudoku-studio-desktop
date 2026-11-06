# Sudoku Studio Desktop

Generate uniquely solvable Sudoku boards, validate entries, and reveal solutions.

[![Build and verify](https://github.com/netcodermike/sudoku-studio-desktop/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/sudoku-studio-desktop/actions/workflows/verify.yml)

**Language:** Java · **Platform:** Windows, macOS, Linux desktop · **App type:** Desktop Sudoku generator and solver

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- 9×9 Swing board
- Backtracking solver
- Unique-solution clue removal
- Entry conflict checks

## Requirements

JDK 17+ and Swing for desktop use; self-tests run headlessly. No external packages.

## Quick start

```sh
git clone https://github.com/netcodermike/sudoku-studio-desktop.git
cd sudoku-studio-desktop
javac -d build src/App.java
java -cp build App
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Generate a puzzle, enter a conflicting digit and check it, correct the digit, reveal the solution, and generate another puzzle.

## Architecture, configuration, and data

App.java starts from a valid patterned Sudoku solution, shuffles removal positions by seed, and removes up to 40 clues only when a capped solver still finds one solution. The same constraints validate user rows/columns/boxes. Self-tests check three seeds, uniqueness, completed solutions, and constraints. State is memory-only.

## Verification

Build with the quick-start command where needed, then run:

```sh
java -cp build App --self-test
```

Manual acceptance: Generate a puzzle, enter a conflicting digit and check it, correct the digit, reveal the solution, and generate another puzzle. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

Puzzle variety comes from clue positions over one base completed grid; difficulty is not rated. No persistence, pencil marks, hints, import, keyboard navigation helpers, or undo. Reveal replaces displayed entries. Validation checks conflicts, not whether an incomplete board can still be completed.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `src/App.java`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
