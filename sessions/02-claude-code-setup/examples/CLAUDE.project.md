# CLAUDE.md — `<project name>`

Per-project instructions for Claude Code. Replace placeholders before committing.

## Project Overview

*(One-paragraph summary: what this code does, who uses it, primary language(s).)*

## Layout

```
c++/                 # library sources
test/c++/            # C++ tests (CTest)
python/              # Python package + bindings
test/python/         # Python tests
docs/                # Sphinx + Doxygen
```

## Build & Test

```bash
cmake -S . -B build -GNinja -DCMAKE_EXPORT_COMPILE_COMMANDS=ON
cmake --build build -j 16
ctest --test-dir build -j 16
```

Build variants: `build_dbg` / `build_san` / `build_prof` → `~/opt/<project>_{dbg,san,prof}`

## Conventions

- *(Coding style, naming, formatting tools — clang-format / ruff / black, etc.)*
- *(Branch strategy: e.g. PRs target `unstable`; rebase before merge)*

## Test Reference Files

- Tests compare against `.ref.h5` files in `test/`. CMake copies them to the build dir at configure time
- After editing a ref in the source tree, also copy it to `build/` (or reconfigure)
- To regenerate: run the test (writes `.out.h5`), copy over `.ref.h5` in both source and build trees, verify the test now passes, confirm only expected quantities changed
- Commit regenerated refs in the *same* commit as the code change, with the reason in the message

## Domain Rules

*(Any non-obvious physics/math constraints. Examples:)*

- *DLR (Discrete Lehmann Representation) is only valid for Green's-function-like objects with a spectral representation. Never apply DLR ops to error bars, uncertainties, or other non-spectral quantities.*
- *(Add others as they trip you up the first time.)*

## Pitfalls

- *(Things that have bitten you that aren't obvious from the code.)*
