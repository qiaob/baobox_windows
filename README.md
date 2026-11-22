# Baobox for Windows

[![Build Windows](https://github.com/qiaob/baobox_windows/actions/workflows/build-windows.yml/badge.svg)](https://github.com/qiaob/baobox_windows/actions/workflows/build-windows.yml)

[English](#english) · [简体中文](#简体中文)

## English

**A tray toolbox for Windows** — screenshots, clipboard history, window management, keep-awake,
keyboard clicking, Claude Code / Codex usage dashboards and a desktop pet, in one native app
with one shortcut system and one settings window. Written in Rust on Win32/GDI; one `.exe`, no
installer, no runtime.

This is the Windows version of [Baobox](https://github.com/qiaob/baobox_mac) (the macOS version
has the most tools). Sibling repositories:

| Repository | |
|---|---|
| [qiaob/baobox_mac](https://github.com/qiaob/baobox_mac) | macOS (Swift) — every tool, plus the user manual |
| [qiaob/baobox_linux](https://github.com/qiaob/baobox_linux) | Linux (Rust + X11) |
| [qiaob/baobox_shared](https://github.com/qiaob/baobox_shared) | The Rust libraries shared by Windows and Linux |

### Tools

| Tool | What it does |
|---|---|
| Screenshot & recording | Hover to capture a window, drag for a region, Enter for the full screen; resize handles and arrow-key nudging; annotation editor (shapes, arrows, pen, highlighter, mosaic, text with IME input, undo); copy / save / pin; scrolling capture; on-screen OCR with the built-in `Windows.Media.Ocr`; screen recording through ffmpeg (`gdigrab`, if installed); history |
| Clipboard | History of text, images and files with a keyboard-driven search panel, paste-back, favorites, text snippets, format detection and conversion (JSON / JWT / XML / URL / timestamp / Base64, QR code), a text editor and pinned text cards; sensitive content (passwords, keys, tokens, card numbers) is skipped by default; history is encrypted at rest with DPAPI |
| Window manager | Halves, quarters, maximize, center, configurable gaps, move across displays, restore the last position — 13 actions, all unbound by default |
| Keep awake | Prevent sleep for a preset time or until turned off |
| Claude Code / Codex assistants | 5-hour and weekly usage windows, cost, recent sessions, resume a session in Windows Terminal |
| Keyboard clicking | Letter labels on every clickable element (UI Automation); type a label to click it |
| Desktop pet | A 3D pet on your desktop (3 built in, 18 more to download) that walks around, sits on windows and shows Baobox notifications as bubbles, with do-not-disturb and a notification history |

Bound out of the box: **Ctrl+Shift+S** (screenshot) and **Ctrl+Shift+V** (clipboard history).
Everything else ships unbound so it can't clash with other apps; set them in Settings.

### Install

Download `Baobox-X.Y.Z-windows-x86_64.zip` from
[Releases](https://github.com/qiaob/baobox_windows/releases), unzip it and run
`baobox-windows.exe`. It lives in the system tray.

Data stays on this PC: settings in `%APPDATA%\Baobox\config.ini`, screenshot and clipboard history
under `%APPDATA%\Baobox\`, screenshots in `Pictures\Baobox` by default. The only network access is
what you ask for: downloading pets (GitHub / jsDelivr, from this repository's `assets/pets/`).

### Build

```powershell
cd baobox-windows
cargo build --release          # target\release\baobox-windows.exe
cargo test
```

On macOS / Linux you can type-check and lint (most tests are `cfg(windows)` and only run on
Windows, which is what CI is for):

```bash
rustup target add x86_64-pc-windows-gnu
cd baobox-windows
cargo +1.90.0 fmt --check
cargo +1.90.0 clippy --all-targets --target x86_64-pc-windows-gnu -- -D warnings
```

The shared crates come from [baobox_shared](https://github.com/qiaob/baobox_shared) by git tag.
Conventions for working on the code: [CLAUDE.md](CLAUDE.md) (Chinese).

### Asset credits

Built-in pets (`baobox-windows/resources/pets/`): BabyPurrPal. Walk cycles
(`baobox-windows/resources/motions/`): Bandai Namco Research Motion Dataset, CC BY-NC 4.0.
Downloadable pets (`assets/pets/`): Quaternius, Kenney, three.js RobotExpressive (Tomás Laulhé),
and two VRoid Hub characters (あわ, マユラ); each pet's author is shown in the app.

History before November 2026 comes from the `windows/` directory of the Baobox monorepo
(`qiaob/baobox_mac`); `#123` in those commit messages refers to issues and PRs there.

## 简体中文

**Windows 托盘效率工具集合** —— 截图、剪贴板历史、窗口管理、防休眠、键盘点击、Claude Code / Codex
用量面板和桌面宠物，一个原生 App，一套快捷键、一个设置窗口。Rust + Win32/GDI 编写；一个 `.exe`，
不用安装，不带运行时。

这是 [Baobox](https://github.com/qiaob/baobox_mac) 的 Windows 版（工具最全的是 macOS 版）。相关仓库：

| 仓库 | |
|---|---|
| [qiaob/baobox_mac](https://github.com/qiaob/baobox_mac) | macOS（Swift）—— 全部工具，以及使用手册 |
| [qiaob/baobox_linux](https://github.com/qiaob/baobox_linux) | Linux（Rust + X11） |
| [qiaob/baobox_shared](https://github.com/qiaob/baobox_shared) | Windows 与 Linux 共用的 Rust 库 |

### 工具

| 工具 | 做什么 |
|---|---|
| 截图与录屏 | 悬停截窗口、拖拽截区域、回车截全屏；八向手柄与方向键微调；标注编辑器（形状、箭头、画笔、荧光笔、马赛克、文字（支持输入法）、撤销）；复制 / 保存 / 贴图；长截图；屏幕取字（系统自带的 `Windows.Media.Ocr`）；录屏（装了 ffmpeg 才有，`gdigrab`）；截图历史 |
| 剪贴板 | 文字、图片、文件的历史，键盘操作的搜索面板，回填粘贴，收藏，文本片段，格式识别与转换（JSON / JWT / XML / URL / 时间戳 / Base64、二维码），文本编辑窗与文字贴片；默认不记录敏感内容（密码、私钥、令牌、银行卡号）；历史落盘用 DPAPI 加密 |
| 窗口管理 | 半屏、四分屏、最大化、居中、可调间距、跨屏移动、恢复上一步 —— 13 个动作，出厂都不绑快捷键 |
| 防休眠 | 按预设时长或一直保持不睡 |
| Claude Code / Codex 助手 | 5 小时与周用量窗口、费用、最近会话，在 Windows Terminal 里续接会话 |
| 键盘点击 | 给每个可点的元素打字母标签（UI Automation），打标签就点下去 |
| 桌面宠物 | 桌面上的 3D 宠物（内置 3 只，另有 18 只可下载），会走动、坐在窗口上，用气泡呈现 Baobox 的通知，带勿扰和通知历史 |

出厂只绑两个快捷键：**Ctrl+Shift+S**（截图）和 **Ctrl+Shift+V**（剪贴板历史）。
其余都不绑，免得和别的程序冲突，在设置里自己配。

### 安装

从 [Releases](https://github.com/qiaob/baobox_windows/releases) 下载
`Baobox-X.Y.Z-windows-x86_64.zip`，解压后运行 `baobox-windows.exe`，它常驻在系统托盘。

数据都在本机：设置在 `%APPDATA%\Baobox\config.ini`，截图与剪贴板历史在 `%APPDATA%\Baobox\` 下，
截图默认存到「图片\Baobox」。只有你主动操作时才联网：下载宠物形象（GitHub / jsDelivr，取本仓库的 `assets/pets/`）。

### 构建

```powershell
cd baobox-windows
cargo build --release          # target\release\baobox-windows.exe
cargo test
```

在 macOS / Linux 上能做类型检查和 lint（大部分测试带 `cfg(windows)`，只在 Windows 上跑，这正是 CI 的用处）：

```bash
rustup target add x86_64-pc-windows-gnu
cd baobox-windows
cargo +1.90.0 fmt --check
cargo +1.90.0 clippy --all-targets --target x86_64-pc-windows-gnu -- -D warnings
```

共享 crate 按 git 标签取自 [baobox_shared](https://github.com/qiaob/baobox_shared)。
改代码的约定见 [CLAUDE.md](CLAUDE.md)。

### 素材来源

内置宠物（`baobox-windows/resources/pets/`）：BabyPurrPal。走路动作（`baobox-windows/resources/motions/`）：
万代南梦宫研究所 Motion Dataset，CC BY-NC 4.0。可下载宠物（`assets/pets/`）：Quaternius、Kenney、
three.js RobotExpressive（Tomás Laulhé），以及 VRoid Hub 的两个角色（あわ、マユラ）；每只宠物的作者在 App 里都有署名。

2026-11 之前的提交历史来自 Baobox 单仓库（`qiaob/baobox_mac`）的 `windows/` 目录，
那些提交信息里的 `#123` 指的是那边的 issue / PR。
