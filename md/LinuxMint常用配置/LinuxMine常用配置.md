# Linux Mint 常用配置

**版本信息**

| 版本号 | 日期       | 作者   | 描述 |
| ------ | ---------- | ------ | ---- |
| v1.0   | 2018-07-08 | kshell |      |

**目录**

[TOC]

## 一：环境

| 项目     | 版本号                         |
| -------- | ------------------------------ |
| 操作系统 | Linux Mint 18.3 Sylvia 64 位   |
| 内核版本 | Linux 4.13.0-43-generic x86_64 |
| 桌面版本 | MATE 1.18.0                    |

## 二：常用配置

### LinuxMint 汉化不完全
- 在安装系统的时候语言包下载速度贼慢，可以先跳过下载，等安装完成后使用国内软件源镜像下载。这时候可出现部分没有汉化的菜单和命令等。
```
sudo apt-get install language-pack-zh-hans language-pack-gnome-zh-hans libreoffice-l10n-zh-cn thunderbird-locale-zh-hans firefox-locale-zh-hans

主要是 language-pack-zh-hans language-pack-gnome-zh-hans
```

### 修复桌面字体

- 系统默认使用楷体，实在太辣眼镜。删除之。

```
sudo apt-get remove fonts-arphic-ukai fonts-arphic-uming
```

### 去掉输入法上的小框框

- fcitx输入法上那个方框框，换来晃去实在不爽。干掉。

```
sudo apt-get remove fcitx-ui-qimpanel
```

### 更改目录结构

- 都用上Linux了。居然桌面目录结构是中文的。土得掉渣，必须换掉。

#### （1）：删除中文目录

```
rm -rf 桌面 音乐 下载 文档 图片 模板 公共的 视频
```

#### （2）：创建目录结构

```
sudo mkdir -p /opt/user
sudo chown kshell:kshell /opt/user
mkdir -p /opt/user/{desktop,downloads,documents/{public,videos,templates,pictures,music}}

ln -sf /opt/user/desktop ~/desktp
ln -sf /opt/user/downloads ~/downloads
ln -sf /opt/user/documents ~/documents
```

#### （3）：修改user-dirs.dirs

- **vim ~/.config/user-dirs.dirs**
- 将如下内容替换进去

```
XDG_DESKTOP_DIR="$HOME/desktop"
XDG_DOWNLOAD_DIR="$HOME/downloads"
XDG_TEMPLATES_DIR="$HOME/documents/templates"
XDG_PUBLICSHARE_DIR="$HOME/documents/public"
XDG_DOCUMENTS_DIR="$HOME/documents"
XDG_MUSIC_DIR="$HOME/documents/music"
XDG_PICTURES_DIR="$HOME/documents/pictures"
XDG_VIDEOS_DIR="$HOME/documents/videos"
```

#### （4）：更新用户目录结构

```
sudo xdg-user-dirs-update
```

### 终端输入密码显示为星号

- 在终端输入密码时，默认什么都没有，改。

- **sudo vim /etc/sudoers**

-  增加一行内容如下

```
Defaults    pwfeedback
```

### 移除开关机闪屏

- 系统默认启动和关机时，就一个图标在屏幕中央晃。
- 不知道系统启动和关机到底有没有进度。
- 还是看着屏幕滚动的日志心里才踏实。
- 打开grub：**sudo vim /etc/default/grub**

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
改成
GRUB_CMDLINE_LINUX_DEFAULT="profile"

sudo update-grub
```

### 修改网卡默认名称

- 以太网卡显示为enp0s25。无线网卡显示为wlp4s。
- 这俩网卡名看着想山寨版似的。修改为eth0 和 wlan0 。
- 打开grub：**sudo vim /etc/default/grub**

```
GRUB_CMDLINE_LINUX=""
改成
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"

sudo update-grub
```

### 配置Samba访问用户和密码

```
smbpasswd -a username
```

## 三：常用软件

### 1:现存软件包

| 软件名称          | 软件包                                 | 描述         |
| ----------------- | -------------------------------------- | ------------ |
| vim               | vim-tiny                               | 编辑器       |
| smplayer          | smplayer smplayer-l10n smplayer-themes | 视频播放器   |
| sublime-text      | sublime-text.deb                       | 编辑器       |
| google-chrome     | google-chrome.deb                      |              |
| qbittorrent       | qbittorrent                            | 下载         |
| uGet              | uget-gtk                               | 下载         |
| iptux             | iptux                                  | 飞鸽         |
| wps               | wps.deb                                | 办公软件     |
| VirtualBox        | VirtualBox.deb                         | 虚拟机       |
| KeePassX          | keepassx                               | 密码存储工具 |
| adobe-flashplugin | adobe-flashplugin                      |              |
| aria2             | aria2                                  |              |
| docker            |                                        |              |
| openssh-server    |                                        |              |
| prelink           |                                        |              |
| preload           |                                        |              |
| zsh               |                                        |              |
| oh-my-zsh         |                                        |              |
|                   |                                        |              |



### 2：配置

sublime-text







<meta http-equiv="refresh" content="1">
