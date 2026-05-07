
【可以查阅的文档】
ArchWiki: https://wiki.archlinux.org/title/Main_page
DMSWiki: https://danklinux.com/
NiriWiki: https://github.com/niri-wm/niri/wiki
ShorinArch: https://shorin.xyz/wiki
Shorin一键配置脚本: https://shorin.xyz/wiki/archsetup

如果出现了两个任务栏可以运行以下命令关掉：
systemctl --user disable --now  dms

如果出现网络问题可以进行以下操作更换wifi后端：
sudo rm /etc/NetworkManager/conf.d/iwd.conf
sudo systemctl restart NetworkManager

【重要工具】
shorindms命令可以对shoridms桌面进行init初始化、update更新、remove移除等操作，操作前都会备份配置文件到.cache下，如果你有东西被意外覆盖可以去找回。详情看shorindms命令的帮助信息。

【Ai助手】
有一个叫作opencode的开源ai助手，默认键位是Mod+Alt+O（英文字母O），有免费模型可以用。如果有查找文件、查询系统信息之类的简单的需求直接询问这个Ai助手，例如："我的快捷键配置文件在哪里？""我要怎么安装软件"等。PS: 谨慎使用ai修改文件。

【重要按键】
super+shift+/ 打开按键教程
super+T 打开终端
super+E 打开文档管理器
super+Z 开始菜单
super+Q 关闭窗口
super+R 按预设切换 宽度
super+F 最大化
Super+alt+F 全屏
super+G/O 切换overview（在overview的时候可以左键移动窗口，滚轮上下切换工作区）
super+alt+A 截图（或者用printscreen键）
super+alt+V 开关剪贴板
super+V 切换浮动窗口
suepr+N 切换浮动窗口聚焦

super+H/L 左右切换聚焦
super+U/i 上下切换工作区
super+右键 调整窗口大小
super+左键 移动窗口
super+滚轮 左右切换聚焦
super+Shift+滚轮 上下切换工作区
super+A/D 左右移动窗口（合并列）
super+shift+F10 下载随机动漫壁纸
【详细按键教程】
所有的键位都可以在.config/niri/dms/binds.kdl里找到

有一些必要设置需要手动完成
1.【overview壁纸】
super+Z打开程序菜单，打开dms设置。进入“个性化-->壁纸”，设置一张壁纸。我在Wallpapers里存放了几张，可以直接使用。然后开启“带模糊效果的壁纸复本”，这是overview的模糊壁纸，super+G或者super+O打开overview就可以看到。

2.【颜色更随壁纸变化】【gtk主题和qt主题】
选择“主题与配色”，点击auto自动，然后选择一个自己喜欢的配色方案。

3.【Firefox颜色同步】
打开firefox之后进入扩展页面，我预装好了pywalfox扩展，点进pywalfox扩展的页面点击右上角的fetch。

【vscode颜色同步】
在vscode里安装DMS主题扩展，然后把主题改成DankShell，再重新更换一次壁纸。

【窗口背景模糊（blur）】
blur已经在26.04实现。我准备了一个预设的blur配置，可以在.config/niri/config.kdl取消末尾blur.kdl相关的include的注释，或者在各个支持blur的软件的配置文件里调整。

【关于文档管理器】
有两个，一个是nautilus（图标是蓝色柜子的那个）一个是thunar，主要用thunar。装两个是因为Niri的录屏依赖xdg-desktop-portal-gnome，而这个portal会依赖nautilus，装都装了，我就把nautius的功能都补全了，也不占什么硬盘资源。

【输入法配置】
super+空格切换输入法。第一次使用输入法有可能无法使用，super+F1重启一下输入法可以解决。
切换到中文之后按f4可以打开菜单。如果出现卡A的情况可以试试按右shift解决。
【输入法Ai大模型联想词】
我自制了`rime-llm-translator`功能，给输入法接入ai进行云拼音联想，还可以在输入法直接跟ai聊天。你可以试试打一些拼音然后输入vv呼叫ai进行处理，还可以试试“call:随便什么指令”。我事先准备的硅基流动的免费模型效果很垃圾，你可以运行`rime-llm-conffig`命令配置你自己的ai。我试下来效果最好的是Gemini。
详情看仓库：https://github.com/SHORiN-KiWATA/rime-llm-translator

【剪贴板同步】
为了解决qq以wayland运行时的剪贴板异常，我自制了linuxqq-clipsync服务，在~/.config/niri/config.kdl中设置了自动启动。如果你因为这个剪贴板同步导致剪贴板出现异常，可以自行删除，如果可以的话麻烦到我的github仓库提交一下bug。

【实用命令】
运行shorin命令可以看到所有可用的便利命令
pac 安装软件(安装软件还可以用bazaar，这是flatpak软件商城)
pacr 卸载软件
mirror-update 更新镜像源
sysup 更新系统
clean 系统清理
quicksave 快速存档
quickload 快速读档

【有趣实用的TUI软件（基于终端的用户交互程序）】
命令：作用
gdu：磁盘空间管理
nmtui：网络配置工具
impala：wifi连接工具，tab键切换，上下左右选择，回车确认（仅支持iwd后端）
btop：终端任务管理器
gtop：dms做的终端任务管理器
yazi：文档管理器
fastfetch：系统信息显示工具

【如果不想要了或者安装有异常可以回档】
如果你是用我的shorin-arch-setup脚本安装的，/usr/local/bin下有两个脚本可以用来回档到运行脚本之前的状态。
回到安装桌面前：shorin-de-undochange
回到运行脚本前：shorin-undochange
如果你是直接用aur包安装的，可以运行shorindms remove

【关于系统维护】
1. 系统更新
请一定使用sysup命令更新系统，不要直接pacman -Syu。更新时要注意是否有重要新闻，sysup命令会在更新前自动创建quicksave-sysup快照，如果更新后出现问题可以从任意快照启动项进入系统运行quickload命令回档（存档读档仅支持btrfs文件系统，使用snapper和btrfs-assistant）

2. 系统清理
clean命令可以清理软件包缓存、回收站、截图、录屏、超数量上限的快照、btrfs备份子卷等内容。clean all命令可以更进一步，清理所有软件包缓存和所有快照。home目录下的.cache文件内的文件也都是可以安全删除的缓存，不过一股脑删除可能会少用户登录什么的，可以使用gdu寻找大文件删除。

3. 快速存档
活用btrfs快照存档，我的quicksave命令可以快速创建描述为quicksave的快照，做不了解的事情记得先快速存档（Mod+F5），我设置了合理的快照数量限制，不用担心快照占用磁盘空间，放心存。

