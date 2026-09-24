<div align="center">
    <img src="./fav.png" alt="RustCode IDE 图标" width="160" />
    <h1>RustCode IDE</h1>
    <h3>为 Rust 开发者打造的开源 IDE · 派生于 VSCodium / Visual Studio Code</h3>
    <p>
        <strong>简体中文</strong> · <a href="./README-EN.md">English</a>
    </p>
    <p>
        <a href="https://github.com/lcmax/RustCode"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-lcmax%2FRustCode-blue" /></a>
        <img alt="License" src="https://img.shields.io/badge/License-MIT-green" />
        <img alt="VS Code 基线" src="https://img.shields.io/badge/VS%20Code%20Baseline-1.126-orange" />
    </p>
</div>

## 简介
<img width="1915" height="1129" alt="image" src="https://github.com/user-attachments/assets/b21c4b6d-ab7e-464f-a738-71480b5d9150" />

**RustCode IDE** 是一款面向 Rust 开发的开源 IDE，基于 **VSCodium**（微软 Visual Studio Code 的 MIT 开源构建）定制而成。它在保留 VS Code 强大编辑体验的同时，开箱即用地内置了完整的 Rust 开发工具链，移除了微软商标与遥测，默认使用开源扩展市场 [open-vsx.org](https://open-vsx.org/)。

> **派生自哪里？** 本项目派生于 [VSCodium](https://github.com/VSCodium/vscodium)，而 VSCodium 是微软 [Visual Studio Code](https://github.com/microsoft/vscode) 源码的 MIT 自由许可构建。因此 RustCode IDE 同样基于 MIT 许可的 VS Code 源码，且默认关闭遥测。

## 特性

- **内置 rust-analyzer 语言服务** —— 开箱即用的代码补全、类型诊断、跳转定义、重构与文档悬浮提示，无需手动安装扩展。
- **内置 CodeLLDB 调试器** —— 基于 [vadimcn.vscode-lldb](https://github.com/vadimcn/codelldb) 的原生 Rust 调试支持，支持断点、变量监视、单步执行。
- **Rust 调试模板与首启引导** —— 内置 `rustide` 扩展，提供 Rust 调试启动模板与首次启动引导（walkthrough），新用户零配置上手。
- **中文界面** —— 内置简体中文语言包，安装即中文，无需额外配置。
- **无遥测、无微软商标** —— 干净构建，默认关闭所有遥测/追踪，数据不外传。
- **开源扩展市场** —— 使用 [open-vsx.org](https://open-vsx.org/) 作为扩展市场（Visual Studio Marketplace 许可不允许非官方构建使用）。
- **现代化界面定制** —— 标题栏集成项目菜单与全局搜索框，内置 Chat 面板（支持豆包 / 千问 / DeepSeek 等 AI 服务）。
- **独立用户数据目录** —— 扩展与配置存放于 `~/.rustcode`，与其他编辑器发行版互不干扰。

## 下载与安装

当前提供 Windows 便携版产物（免安装）：

| 平台 | 产物 |
|------|------|
| Windows x64 | `VSCode-win32-x64-new2/`（直接运行 `RustCode.exe`） |

- 用户数据目录：`%USERPROFILE%\.rustcode`
- 主程序：`RustCode.exe`（界面显示名仍为 “RustCode IDE”）

## 从源码构建

本项目在本地完成全部构建，无需依赖 GitHub Actions：

```bash
# 1. 准备源码（clone vscode 上游并打补丁）
./prepare_vscode.sh

# 2. 正规重建（注入 Rust 扩展 + 品牌配置 + 官方打包链，Windows 一键）
#    在 Git Bash 下执行：
"C:\Program Files\Git\bin\bash.exe" ./dev/rebuild_rustcode.sh

# 产物输出至 VSCode-win32-x64-new2/
```

三平台（Windows / Linux / macOS）Release 发布已提供 GitHub Actions 工作流 [.github/workflows/rustcode-release.yml](.github/workflows/rustcode-release.yml)，手动触发或推送 `v*` 标签即可产出并上传各平台归档。

## 项目结构

```text
.
├── vscode/                    # VS Code / VSCodium 源码（构建输入，codeload 平铺 + 本地补丁）
├── extensions/                # 内置 Rust 扩展源（rust-analyzer / CodeLLDB / rustide）
├── src/stable/  src/insider/  # 品牌化资源源（图标、product.json 片段，prepare 时并入）
├── dev/rebuild_rustcode.sh    # Windows 一键重建脚本
├── prepare_vscode.sh          # 源码准备与品牌注入
├── .github/workflows/         # 三平台 Release 工作流
└── assets/                    # 图标等设计资产
```

## 感谢

本项目站在众多优秀开源项目与社区的肩上，特此致谢：

- [Microsoft Visual Studio Code](https://github.com/microsoft/vscode) 团队 —— 上游编辑器源码（MIT License）
- [VSCodium](https://github.com/VSCodium/vscodium) 社区 —— 自由许可构建链、无遥测默认配置
- [rust-analyzer](https://github.com/rust-lang/rust-analyzer) 团队 —— Rust 语言服务
- [vadimcn](https://github.com/vadimcn) —— [CodeLLDB](https://github.com/vadimcn/codelldb) 调试器
- [open-vsx.org](https://open-vsx.org/) —— 开源扩展市场
- 简体中文语言包维护者（MS-CEINTL）
- 以及所有为本项目提出建议与反馈的用户

## 许可证

[MIT](LICENSE)

本项目的直接派生前缀为 VSCodium（MIT），最终上游为微软 VS Code 源码（MIT），不包含任何微软商标、遥测与专有组件。

---

**作者**：lcmax &lt;lcmax@163.com&gt; · [GitHub](https://github.com/lcmax/RustCode)
