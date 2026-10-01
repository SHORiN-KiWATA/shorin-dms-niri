# shorin-dms-niri

基于Niri+DMS的桌面预设，开箱即用。


##  Usage 使用方法

- install安装

    ```
    yay -S shorin-dms-niri-git
    ```

    ```
    shorindms init 
    ```

    启动niri：
    
    ```
    niri-session
    ```

    如果你使用显示管理器的话在登录界面切换为niri

- update更新

    ```
    shorindms update
    ```
    以防万一，你的配置文件会被备份到`.cache`。

- uninstall卸载

    ```
    shorindms remove 
    ```

    ```
    yay -Rns shorin-dms-niri-git
    ```

## QQ

预装了 [linuxqq-wayland-fix](https://github.com/SHORiN-KiWATA/linuxqq-wayland-fix)，修复 QQ 以 Wayland 运行时屏幕共享、共享电脑声音和剪贴板的问题。请从应用菜单的「QQ（Wayland修复版）」打开 QQ。
