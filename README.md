# Quake Modoki

[![Crates.io Version](https://img.shields.io/crates/v/quake-modoki)](https://crates.io/crates/quake-modoki)

![Demo](assets/demo.gif)

Windows utility enabling Quake Mode behavior—any window slides in/out from screen edge via global hotkey.

## Features

- 🎯 **Track any window** — Register current foreground window via `Ctrl+Alt+Q`
- 🎬 **Smooth slide animation** — 200ms cubic easing, DWM frame-synced
- 🧭 **Smart direction detection** — Auto-detect slide direction from window position
- 👁️ **Auto-hide on focus loss** — Window slides out when focus changes
- 🔄 **State preservation** — Original position/size/z-order restored on untrack
- 🖥️ **System tray** — Status, Untrack, Start with Windows, Exit
- 🔔 **Desktop notification** — Toast when window tracked
- 🚀 **Auto-launch** — Optional startup with Windows (Registry-based)
- 🖱️ **Edge trigger** — Show/hide by moving cursor to screen edge (toggleable)
- ⌨️ **Configurable hotkeys** — Override hotkeys via config file
- 🧾 **Open config from tray** — Quick access to the config file via tray menu

## Installation

```bash
cargo install quake-modoki --locked
```

## Usage

| Hotkey | Action |
|--------|--------|
| `Ctrl+Alt+Q` | Track current window |
| `F8` | Toggle window visibility |

Tray icon menu: Untrack / Open config file / Edge trigger / Start with Windows / Exit

### Config

Hotkeys are loaded from the config file. The easiest way to find it is:

1. Right-click the tray icon
2. Select `Open config file`

Example:

```toml
version = 1

[shortcuts]
toggle = "F8"
track = "Ctrl+Alt+Q"
```

## Development

### Pre-commit Hooks

```bash
# prek install
cargo install --locked prek

# enable hooks
prek install
```

Hooks: `cargo fmt`, `cargo clippy`, `typos`, `trailing-whitespace`, etc.

## Made with

- Icon: Nano Banana Pro (Gemini 3 Pro Image Preview)
- Code: [Claude Code](https://claude.ai/code)

## License

MIT OR Apache-2.0
