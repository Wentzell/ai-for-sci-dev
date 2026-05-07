# Development Context

- Scientific software development (C++ and Python)
- HPC / cluster work on Flatiron systems

## Communication

- Don't assume the user is correct — push back when something looks off
- Be concise; reach for tools rather than narrating intent

## Environment

- `$HOME` (`~`) is on NFS, shared with cluster nodes — avoid large recursive `find` / `grep` / `rg` sweeps over `~`
- Local-disk Dropbox is preferable for searches when available
- Inside a git repo, prefer `git grep` over filesystem walks

## Software Stack

- LMod modules; default env: `module show devenv9/clang-py3-mkl`
- Extra libraries in `~/opt/`

## Tools

- Compiler: Clang (preferred) or GCC
- Build: Ninja (preferred) or Make
- Don't invoke the compiler directly — always go through CMake
- Run tests from their own directory so reference files resolve

## Common Commands

- Configure: `cmake -S . -B build -GNinja -DCMAKE_EXPORT_COMPILE_COMMANDS=ON`
- Sanitizers: `-DASAN=ON -DUBSAN=ON`
- Test: `ctest --test-dir build -j 16` (always use ctest; raw `python test.py` may load the installed module instead of the build version)

## Git Workflow

- Feature branches → unstable; clean up history and rebase rather than merge
- Pre-authorized to create commits without per-commit confirmation
- Hold off on `push`, `push --force`, amending published commits, destructive resets/checkouts, and history rewrites on shared branches unless asked

## Debugging

- Sanitizer build (ASAN/UBSAN) for segfaults, memory errors, NaN tracking — release builds give cryptic crashes
