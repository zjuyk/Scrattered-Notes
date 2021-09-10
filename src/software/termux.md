# termux

- 换源

  - 不建议手动更改源列表，可以采用 `termux-change-repo` 这个官方工具

- 添加额外按键

    ```bash
    ~/.termux/termux.properties # 设置文件

    extra-keys = [['ESC','/','-','HOME','UP','END','PGUP'],['TAB','CTRL','ALT','LEFT','DOWN','RIGHT','PGDN']] # 加入这行
    ```

- 安装 Arch

    - `proot-distro` 这个官方包非常好用
        ```bash
        proot-distro install archlinux # 安装
        proot-distro login archlinux # 进入
        ```

- 个性化

    - 主要是终端配色和命令提示符
    - 直接 fish 一把梭，注意 `fish_config` 的 webui 依赖 python，所以需要先安装 python

- SSH

    - 注意 termux ssh 的监听端口默认为 8022 而不是 22

- 后台运行

    - 注意安卓会杀掉长期不活动的后台应用，小心滚到一半安卓把 termux 杀掉了，一定要后台锁定！！！
