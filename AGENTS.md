# Repository Guidelines

## Project Structure & Modules
- Core Ada sources live in `src/` (pairs of `.ads` specs and `.adb` bodies such as `language-tree.ads` / `language-tree.adb`).
- Build artifacts go to `obj/` and should not be edited or committed.
- The main project file is `language.gpr`; `alire.toml` defines the crate metadata and dependencies.

## Build, Test, and Development
- Build with Alire: `alr build -- -P language.gpr` (honors `BUILD` and `LIBRARY_TYPE` externals from `alire.toml`).
- Direct GPR build (if Alire is unavailable): `gprbuild -P language.gpr`.
- Use `BUILD=Coverage` or `BUILD=Debug` when investigating issues, e.g. `BUILD=Debug alr build -- -P language.gpr`.

## Coding Style & Naming
- Follow existing Ada style: 3‑space indentation, aligned `is`/`return`, and 80‑column friendly lines.
- Keep package/file naming consistent with the current scheme (`language-*.ads/.adb`, `Language.*` package hierarchy).
- Preserve existing license headers and comments; do not add new copyright blocks.

## Testing Guidelines
- There is no standalone test suite in this crate yet; rely on `alr build` to remain warning‑free and link‑clean.
- New features and bug fixes should include Ada tests when reasonable (e.g. using AUnit or the downstream integration harness).
- Prefer small, focused changes that are easy to exercise from the GNAT Studio/LSP client side.

## Commit & Pull Request Practices
- Use clear, imperative commit subjects (e.g. `Refine construct tree navigation`, `Fix C analyzer ranges`).
- Group related edits into a single commit; avoid mixing refactors with behavior changes.
- For pull requests, include: a short problem/solution summary, key files touched, how you built/tested (`alr build ...`), and links to any related issues.

## Agent-Specific Notes
- When modifying `src/`, preserve existing formatting and naming patterns; prefer minimal, surgical diffs.
- Do not alter `alire.toml` or `language.gpr` externals unless the change is part of the requested task.
