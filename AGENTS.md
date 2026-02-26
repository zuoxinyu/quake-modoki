# Repository Guidelines

## Project Structure & Module Organization
- `src/main.rs` is the entry point and event loop coordinator.
- Feature modules live in `src/` (for example: `animation.rs`, `tracking.rs`, `edge.rs`, `tray.rs`, `autolaunch.rs`).
- Build metadata is in `Cargo.toml` and `build.rs`.
- Static assets (icon/demo media) are in `assets/`.
- CI is defined in `.github/workflows/ci.yml`.
- Tests are mostly inline unit tests (`mod tests`) inside each Rust module.

## Build, Test, and Development Commands
- `cargo build --verbose`: compile the app locally.
- `cargo run`: run the utility in development mode.
- `cargo test --verbose`: run all unit tests.
- `cargo fmt --check`: verify formatting matches `rustfmt`.
- `cargo clippy --all-targets --all-features -- -D warnings`: lint with warnings treated as errors (matches CI).
- Optional pre-commit flow:
  - `cargo install --locked prek`
  - `prek install`

## Coding Style & Naming Conventions
- Use standard Rust formatting (`cargo fmt`); CI enforces format and lint checks.
- Naming:
  - modules/files: `snake_case` (for example `edge.rs`)
  - functions/variables: `snake_case`
  - types/traits: `UpperCamelCase`
  - constants/statics: `UPPER_SNAKE_CASE`
- Prefer small, focused modules and explicit error paths (`anyhow`/`thiserror`) over panics in runtime code.

## Testing Guidelines
- Add unit tests near implementation (`mod tests { ... }`) in the same file.
- Use descriptive test names that state behavior (for example `restores_original_bounds_on_untrack`).
- Some Windows/registry-related tests may require serialization; use `serial_test` where shared state exists.
- Run `cargo test --verbose` before opening a PR.

## Commit & Pull Request Guidelines
- Follow the repository’s commit style: short imperative subject, often emoji-prefixed (examples: `🐛 Fix ...`, `✨ Add ...`, `📝 Update ...`).
- Keep commits scoped to one logical change.
- PRs should include:
  - clear summary of behavior changes,
  - linked issue (if applicable),
  - test/lint status (`cargo fmt`, `cargo clippy`, `cargo test`),
  - screenshots/GIFs for tray/UI-visible behavior changes.
