<div align="center">
    <img src="./fav.png" alt="RustCode IDE logo" width="160" />
    <h1>RustCode IDE</h1>
    <h3>An open-source IDE for Rust developers · Derived from VSCodium / Visual Studio Code</h3>
    <p>
        <a href="./README.md">简体中文</a> · <strong>English</strong>
    </p>
    <p>
        <a href="https://github.com/lcmax/RustCode"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-lcmax%2FRustCode-blue" /></a>
        <img alt="License" src="https://img.shields.io/badge/License-MIT-green" />
        <img alt="VS Code Baseline" src="https://img.shields.io/badge/VS%20Code%20Baseline-1.126-orange" />
    </p>
</div>

## Introduction

**RustCode IDE** is an open-source IDE built for Rust development, customized from **VSCodium** — the MIT-licensed, freely-licensed build of Microsoft's Visual Studio Code. It keeps the full editing experience of VS Code while shipping with a complete, ready-to-use Rust toolchain, removes Microsoft trademarks and telemetry, and defaults to the open-source extension marketplace [open-vsx.org](https://open-vsx.org/).

> **Where does it come from?** This project is derived from [VSCodium](https://github.com/VSCodium/vscodium), which in turn is the MIT-licensed build of Microsoft's [Visual Studio Code](https://github.com/microsoft/vscode) source. RustCode IDE therefore also builds on the MIT-licensed VS Code source, with telemetry disabled by default.

## Features

- **Bundled rust-analyzer** — code completion, diagnostics, go-to-definition, refactoring and hover docs work out of the box, no extension installation required.
- **Bundled CodeLLDB debugger** — native Rust debugging powered by [vadimcn.vscode-lldb](https://github.com/vadimcn/codelldb): breakpoints, variable inspection, step execution.
- **Rust debug templates & first-run guide** — the built-in `rustide` extension provides debug launch templates and a first-run walkthrough so new users can start with zero configuration.
- **Simplified Chinese UI** — the zh-hans language pack is bundled; the interface is in Chinese after installation.
- **No telemetry, no Microsoft trademarks** — a clean build with all telemetry/tracking disabled by default; no data leaves your machine.
- **Open-source marketplace** — extensions are served from [open-vsx.org](https://open-vsx.org/) (the Visual Studio Marketplace license does not permit non-official builds).
- **Modernized UI** — a title bar with project menu and a global search box, plus a built-in Chat panel (Doubao / Qwen / DeepSeek AI services).
- **Dedicated user data directory** — extensions and config live under `~/.rustcode`, isolated from other editor distributions.

![Uploading image.png…]()


## Download & Install

A portable Windows build is currently provided (no installation required):

| Platform | Artifact |
|----------|----------|
| Windows x64 | `VSCode-win32-x64-new2/` (run `RustCode.exe` directly) |

- User data directory: `%USERPROFILE%\.rustcode`
- Main executable: `RustCode.exe` (display name remains "RustCode IDE")

## Build from Source

The whole build runs locally — no dependency on GitHub Actions:

```bash
# 1. Prepare the source tree (clone upstream vscode and apply patches)
./prepare_vscode.sh

# 2. Full rebuild (inject Rust extensions + branding + official packaging chain, Windows one-shot)
#    Run inside Git Bash:
"C:\Program Files\Git\bin\bash.exe" ./dev/rebuild_rustcode.sh

# Artifacts are emitted to VSCode-win32-x64-new2/
```

A three-platform (Windows / Linux / macOS) release workflow is provided at [.github/workflows/rustcode-release.yml](.github/workflows/rustcode-release.yml). Trigger it manually or by pushing a `v*` tag to build and upload platform archives.

## Repository Layout

```text
.
├── vscode/                    # VS Code / VSCodium source (build input; codeload tarball + local patches)
├── extensions/                # Bundled Rust extensions source (rust-analyzer / CodeLLDB / rustide)
├── src/stable/  src/insider/  # Branding resources source (icons, product.json fragments; merged by prepare)
├── dev/rebuild_rustcode.sh    # Windows one-click rebuild script
├── prepare_vscode.sh          # Source preparation & branding injection
├── .github/workflows/         # Three-platform release workflows
└── assets/                    # Design assets (icons)
```

## Acknowledgements

This project stands on the shoulders of many great open-source projects and communities:

- [Microsoft Visual Studio Code](https://github.com/microsoft/vscode) team — the upstream editor source (MIT License)
- [VSCodium](https://github.com/VSCodium/vscodium) community — the freely-licensed build chain and telemetry-free defaults
- [rust-analyzer](https://github.com/rust-lang/rust-analyzer) team — the Rust language server
- [vadimcn](https://github.com/vadimcn) — the [CodeLLDB](https://github.com/vadimcn/codelldb) debugger
- [open-vsx.org](https://open-vsx.org/) — the open-source extension marketplace
- Simplified Chinese language pack maintainers (MS-CEINTL)
- And every user who has provided feedback and suggestions

## License

[MIT](LICENSE)

This project is directly derived from VSCodium (MIT) and ultimately from the Microsoft VS Code source (MIT). It contains no Microsoft trademarks, telemetry, or proprietary components.

---

**Author**: lcmax &lt;lcmax@163.com&gt; · [GitHub](https://github.com/lcmax/RustCode)
