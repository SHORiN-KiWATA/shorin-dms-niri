# Shorin DMS Niri 使用方法

## 可以查阅的文档

- ArchWiki: <https://wiki.archlinux.org/title/Main_page>
- DMS Wiki: <https://danklinux.com/>
- Niri Wiki: <https://github.com/niri-wm/niri/wiki>
- ShorinArch: <https://shorin.xyz/wiki>
- Shorin 一键配置脚本: <https://shorin.xyz/wiki/archsetup>

## 常见问题

如果出现了两个任务栏，可以运行以下命令关掉：

```bash
systemctl --user disable --now dms
```

如果出现网络问题，可以进行以下操作更换 WiFi 后端：

```bash
sudo rm /etc/NetworkManager/conf.d/iwd.conf
sudo systemctl restart NetworkManager
```

## 重要工具

`shorindms` 命令可以对 Shorin DMS 桌面进行 `init` 初始化、`update` 更新、`remove` 移除等操作。操作前都会备份配置文件到 `~/.cache` 下，如果你有东西被意外覆盖可以去找回。详情看 `shorindms` 命令的帮助信息。

## AI 助手

### Miyu

<https://github.com/SHORiN-KiWATA/Miyu>

Miyu 是我做的 AI 助手，已集成进终端，终端打字直接无缝对话。

- 运行 `miyu normal` 进入普通模式的 TUI
- 运行 `miyu dev` 进入开发模式的 TUI
- 运行 `miyu config` 进行自定义配置，支持自定义提示词、供应商、模型

如果有问题可以先询问这个 AI 助手。

默认使用的模型是 opencodezen 的公共密钥，但是他们砍了公共密钥的额度，所以对话几次就没额度了，建议配一个自己的，可以去 opencode 的官网注册一个 opencodezen 的账号用它们的免费额度。

#### 卸载

想移除 Miyu 的话运行下面的命令：

```bash
# 先移除和终端的集成
miyu remove-shell-hook

# 然后删除包
yay -Rns miyu
```

## 重要按键

| 按键 | 作用 |
|---|---|
| `Super+Shift+/` | 打开按键教程 |
| `Super+T` | 打开终端 |
| `Super+E` | 打开文档管理器 |
| `Super+Z` | 开始菜单 |
| `Super+Q` | 关闭窗口 |
| `Super+R` | 按预设切换宽度 |
| `Super+F` | 最大化 |
| `Super+Alt+F` | 全屏 |
| `Super+G` / `Super+O` | 切换 overview（在 overview 的时候可以左键移动窗口，滚轮上下切换工作区） |
| `Super+Alt+A` | 截图（或者用 `PrintScreen` 键） |
| `Super+Alt+V` | 开关剪贴板 |
| `Super+V` | 切换浮动窗口 |
| `Super+N` | 切换浮动窗口聚焦 |
| `Super+H` / `Super+L` | 左右切换聚焦 |
| `Super+U` / `Super+I` | 上下切换工作区 |
| `Super+右键` | 调整窗口大小 |
| `Super+左键` | 移动窗口 |
| `Super+滚轮` | 左右切换聚焦 |
| `Super+Shift+滚轮` | 上下切换工作区 |
| `Super+A` / `Super+D` | 左右移动窗口（合并列） |
| `Super+Shift+F10` | 下载随机动漫壁纸 |

所有的键位都可以在 `~/.config/niri/dms/binds.kdl` 里找到。

## 需要手动完成的设置

### 1. Overview 壁纸

`Super+Z` 打开程序菜单，打开 DMS 设置。进入「个性化 → 壁纸」，设置一张壁纸，我在 Wallpapers 里存放了几张，可以直接使用。然后开启「带模糊效果的壁纸复本」，这是 overview 的模糊壁纸，`Super+G` 或者 `Super+O` 打开 overview 就可以看到。

### 2. 颜色跟随壁纸变化（GTK 主题和 Qt 主题）

选择「主题与配色」，点击 auto 自动，然后选择一个自己喜欢的配色方案。

### 3. Firefox 颜色同步

打开 Firefox 之后进入扩展页面，我预装好了 pywalfox 扩展，点进 pywalfox 扩展的页面点击右上角的 fetch。

### 4. VSCode 颜色同步

在 VSCode 里安装 DMS 主题扩展，然后把主题改成 DankShell，再重新更换一次壁纸。

## 窗口背景模糊（blur）

blur 已经在 26.04 实现。我准备了一个预设的 blur 配置，可以在 `~/.config/niri/config.kdl` 取消末尾 `blur.kdl` 相关 include 的注释，或者在各个支持 blur 的软件的配置文件里调整。

## 关于文档管理器

有两个，一个是 nautilus（图标是蓝色柜子的那个），一个是 thunar，主要用 thunar。装两个是因为 Niri 的录屏依赖 xdg-desktop-portal-gnome，而这个 portal 会依赖 nautilus，装都装了，我就把 nautilus 的功能都补全了，也不占什么硬盘资源。

## 输入法

- `Super+空格` 或者 `Ctrl+空格` 切换输入法。第一次使用输入法有可能无法使用，`Mod+F1` 开关一下输入法可以解决。
- 切换为中文后输入时按下 `F4` 可以打开菜单。如果出现卡 A 的情况可以试试按右 `Shift` 解决。
- 使用 `fcitx5-configtool` 命令或者打开应用菜单里的「fcitx5 配置」可以对输入法进行细节配置。
- 如果输入法出现异常，看这个页面：<https://github.com/SHORiN-KiWATA/Shorin-ArchLinux-Guide/wiki/%E4%B8%AD%E6%96%87%E8%BE%93%E5%85%A5%E6%B3%95>，通常能解决问题，如果无法解决可以在交流群询问。

### 输入法 AI 大模型联想词

<https://github.com/SHORiN-KiWATA/rime-llm-translator>

我自制了 `rime-llm-translator` 功能，给输入法接入 AI 进行拼音联想，还可以在输入法直接跟 AI 聊天。你可以试试打一些拼音然后输入 `vv` 呼叫 AI 进行处理，还可以试试 `call:随便什么指令`。我事先准备的免费模型效果和额度都一般，你可以运行 `rime-llm-config` 命令配置你自己的 AI。

#### 移除该功能

可以按照如下步骤删除 rime-llm-translator。

1. 删除 `~/.local/share/fcitx5/rime/rime.lua` 中的这一行：

    ```lua
    llm_translator = require("llm_translator")
    ```

2. 删除 `~/.local/share/fcitx5/rime/rime_ice.custom.yaml` 中的三条 patch：

    ```yaml
      # 1. 扩充允许输入的字符集：允许在拼音中直接输入指定的标点符号，阻止其直接上屏
      "speller/alphabet": "zyxwvutsrqponmlkjihgfedcba.,?'!:<>\\/"
      # 2. 将 Lua AI 脚本 (llm_translator) 强行插入到处理列表的第 0 位之前
      "engine/translators/@before 0": lua_translator@llm_translator
      # 3. 定义正则捕获规则：把输入当成不可分割的整体喂给 AI 脚本处理
      "recognizer/patterns/llm_pinyin": "^[a-z][a-z.,?'!:<>/\\\\]*$"
    ```

3. 移除缓存、配置和软件包：

    ```bash
    gio trash ~/.config/rime-llm-translator ~/.cache/rime-llm-translator ~/.cache/rime-llm-translator-backup/
    yay -Rns rime-llm-translator-git
    ```

## 剪贴板同步

<https://github.com/SHORiN-KiWATA/linuxqq-clipsync>

为了解决 QQ 以 Wayland 运行时的剪贴板异常，我自制了 linuxqq-clipsync 服务，在 `~/.config/niri/config.kdl` 中设置了自动启动。如果你因为这个剪贴板同步导致剪贴板出现异常，可以自行删除，如果可以的话麻烦到我的 GitHub 仓库提交一下 bug。

## 安装和卸载软件

- `pac` 命令安装软件。安装 AUR 软件时使用 AI 审核安装脚本，不建议跳过该审核环节，AUR 是无审查的，脚本可能存在风险。
- `pacr` 命令卸载软件，卸载时可选使用 AI 查找软件残留。
- `bazaar` 是美观的图形化 Flatpak 软件商城。

## 实用命令

| 命令 | 作用 |
|---|---|
| `mirror-update` | 更新镜像源 |
| `sysup` | 更新系统 |
| `clean` | 系统清理 |
| `quicksave` | 快速存档 |
| `quickload` | 快速读档 |

运行 `shorin` 命令可以看到所有可用的便利命令。

## 有趣实用的 TUI 软件

TUI 即基于终端的用户交互程序。

| 命令 | 作用 |
|---|---|
| `gdu` | 磁盘空间管理 |
| `nmtui` | 网络配置工具 |
| `btop` | 终端任务管理器 |
| `gtop` | DMS 做的终端任务管理器 |
| `yazi` | 文档管理器 |
| `fastfetch` | 系统信息显示工具 |

## 运行 Windows 软件

<https://github.com/SHORiN-KiWATA/proton-wrapper>

此功能由 `shorin-proton-wrapper-git` AUR 包提供。双击 `.exe` 文件会自动用「运行 Windows 软件」打开，会自动使用 DW-Proton 在 `~/.proton` 目录初始化运行环境。

如果用「设置 Windows 软件运行环境」打开的话可以进行各种自定义设置，如运行器、MangoHud 屏显（帧数、硬件占用之类的）、GameScope（如果遇到窗口异常、交互异常的话可以尝试用 GameScope 打开）等。

如果 DW-Proton 无法运行软件，可以试试用 GE-Proton；如果连 GE-Proton 也不行，别的大概率也不行，建议从环境变量、运行参数入手解决问题，或者尝试兼容层以外的运行方案。

## 如果不想要了或者安装有异常可以回档

如果你是用我的 shorin-arch-setup 脚本安装的，`/usr/local/bin` 下有两个脚本可以用来回档到运行脚本之前的状态：

- 回到安装桌面前：`shorin-de-undochange`
- 回到运行脚本前：`shorin-undochange`

如果你是直接用 AUR 包安装的，可以运行 `shorindms remove`。

## 关于系统维护

### 1. 系统更新

请一定使用 `sysup` 命令更新系统，不要直接 `pacman -Syu`。更新时要注意是否有重要新闻。`sysup` 命令会在更新前自动创建 `quicksave-sysup` 快照，如果更新后出现问题可以从任意快照启动项进入系统运行 `quickload` 命令回档。

> 存档读档仅支持 btrfs 文件系统，使用 snapper 和 btrfs-assistant。

### 2. 系统清理

`clean` 命令可以清理软件包缓存、回收站、截图、录屏、超数量上限的快照、btrfs 备份子卷等内容。`clean all` 命令可以更进一步，清理所有软件包缓存和所有快照。

home 目录下 `.cache` 内的文件也都是可以安全删除的缓存，不过一股脑删除可能会少用户登录什么的，可以使用 `gdu` 寻找大文件删除。

### 3. 快速存档

活用 btrfs 快照存档。我的 `quicksave` 命令可以快速创建描述为 quicksave 的快照，做不了解的事情记得先快速存档（`Mod+F5`）。我设置了合理的快照数量限制，不用担心快照占用磁盘空间，放心存。
