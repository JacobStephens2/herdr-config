# Herdr Configuration

Personal configuration for [Herdr](https://herdr.dev) terminal workspace manager, featuring optimized keybindings for workspace navigation.

## Setup

Symlink `config.toml` to your Herdr configuration directory:

```bash
mkdir -p ~/.config/herdr
ln -sf "$PWD/config.toml" ~/.config/herdr/config.toml
```

If Herdr is already running, reload the configuration:

```bash
herdr server reload-config
```

Or press `Ctrl+b`, then `Shift+r` inside Herdr.

## Configured Keybindings

All shortcuts use the default prefix `Ctrl+b` (press and release `Ctrl+b`, then press the action key).

### Workspace Navigation

| Action | Shortcut | Description |
| :--- | :--- | :--- |
| **Next Workspace** | `Ctrl+b` then `]` *(or `)`)* | Switch to next workspace |
| **Previous Workspace** | `Ctrl+b` then `[` *(or `(`)* | Switch to previous workspace |
| **Jump to Workspace 1–9** | `Ctrl+b` then `Shift+1..9` (`!`, `@`, `#`...) | Directly switch to workspace by index |
| **Workspace Picker** | `Ctrl+b` then `w` | Open interactive visual workspace navigator |
| **Goto Navigator** | `Ctrl+b` then `g` | Open fuzzy session / workspace / tab search modal |
| **New Workspace** | `Ctrl+b` then `Shift+n` | Create a new workspace |
| **Rename Workspace** | `Ctrl+b` then `Shift+w` | Rename active workspace |
| **Close Workspace** | `Ctrl+b` then `Shift+d` | Close active workspace |

### Copy Mode & Tabs

- **Copy Mode**: `Ctrl+b` then `Esc` *(rebound from `[` to prevent collision with Previous Workspace; mouse drag-select also copies natively)*
- **Switch Tabs**: `Ctrl+b` then `1..9`
- **Next / Previous Tab**: `Ctrl+b` then `n` / `p`
- **New Tab**: `Ctrl+b` then `c`
- **Close Tab**: `Ctrl+b` then `Shift+x`
