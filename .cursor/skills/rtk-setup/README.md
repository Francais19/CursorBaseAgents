---
name: rtk-setup
description: Install, verify, and troubleshoot RTK (Rust Token Killer). Use when RTK is missing, commands fail, or the user asks about RTK setup.
---

# RTK Setup

## When to use

- RTK is not installed (`command not found: rtk`)
- User asks how to set up or configure RTK
- `rtk gain` fails (wrong package installed)
- Troubleshooting token optimization issues

## Installation

### Homebrew (recommended, macOS/Linux)

```bash
brew install rtk
```

### Quick install (Linux/macOS)

```bash
curl -fsSL https://raw.githubusercontent.com/rtk-ai/rtk/refs/heads/master/install.sh | sh
```

Installs to `~/.local/bin`. Add to PATH if needed:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc  # or ~/.bashrc
source ~/.zshrc
```

### Cargo (from source)

```bash
cargo install --git https://github.com/rtk-ai/rtk
```

**Do not use `cargo install rtk`** -- that installs a different package (Rust Type Kit).

### Windows

#### Prebuilt binary (recommended on Windows)

1. Download the Windows 10 `exe` archive from:

```text
https://github.com/rtk-ai/rtk
```

2. Extract the archive.

3. Add the folder containing `rtk.exe` to `PATH`.

Example:

```text
C:\Tools\rtk
```

4. Restart PowerShell and verify the installation:

```powershell
rtk --version
```

Expected output:

```text
rtk 0.31.0
```

If RTK is installed successfully, initialize it for your AI tool:

```bash
# 1. Install for your AI tool
rtk init -g                     # Claude Code / Copilot (default)
rtk init -g --gemini            # Gemini CLI
rtk init -g --codex             # Codex (OpenAI)
rtk init -g --agent cursor      # Cursor
rtk init --agent windsurf       # Windsurf
rtk init --agent cline          # Cline / Roo Code
```

Then restart your AI tool and test it:

```bash
git status  # Automatically rewritten to rtk git status
```

## Verification

Run both commands to confirm correct installation:

```bash
rtk --version   # Should show "rtk 0.29.0" or similar
rtk gain         # Should show token savings stats (not an error)
```

If `rtk gain` returns an error, uninstall and reinstall using the methods above:

```bash
cargo uninstall rtk              # if installed via cargo
brew uninstall rtk               # if installed via homebrew
```

## Configuration

Config file location:
- Linux: `~/.config/rtk/config.toml`
- macOS: `~/Library/Application Support/rtk/config.toml`
- Windows: `%AppData%\rtk\config.toml`

Example config:

```toml
[hooks]
exclude_commands = ["curl", "playwright"]

[tee]
enabled = true
mode = "failures"
max_files = 20
```

## Token savings analytics

```bash
rtk gain                # Summary stats
rtk gain --graph        # ASCII graph (last 30 days)
rtk gain --history      # Recent command history
rtk discover            # Find missed savings opportunities
```

## Uninstall

```bash
brew uninstall rtk       # if installed via homebrew
cargo uninstall rtk      # if installed via cargo
```

## Resources

- Repository: https://github.com/rtk-ai/rtk
- Troubleshooting: https://github.com/rtk-ai/rtk/blob/master/docs/TROUBLESHOOTING.md
- Architecture: https://github.com/rtk-ai/rtk/blob/master/ARCHITECTURE.md
