# 记录一次arch linux 系统安装及美化
### 一、基础系统的安装
根据官方的安装指南安装好系统
安装时 按转 base 和 base-devel 两个软件包组
如果需要 ifconfig等命令管理网络 还需安装net-tools 包组
### 二、系统配置
#### 网络配置
安装 networkmanager 软件
启动服务并设置开机自动运行

```bash
pacman -S networkmanager
systemctl start NetworkManager.servcie
systemctl enable NetworkManager.service
```
#### 创建新用户
```bash
useradd -m -G users -g wheel 用户名
```

shell推荐使用zsh
```bash
pacman -S zsh
usermod -s /bin/zsh 用户名
```
#### 安装驱动和xorg服务

nvidia

```bash
pacman -S xorg-drivers
pacman -S mesa nvidia nvidia-settings xorg-xinit xorg-server
```
amd

```bash
pacman -S xorg-drivers
pacman -S xorg-xinit xorg-server mesa
```

#### 设置国内社区软件源

向 /etc/pacman.conf 文件 加入如下内容
安装 archlinuxcn-keyring 包
```
[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
```bash
pacman -Sy archlinuxcn-keyring
```
#### 安装中文字体
arch wiki 上有 fonts 页面
#### 安装i3-gaps 及其他软件
```bash
pacman -S i3-gaps dunst rofi compton thunar 
```

####  安装polybar 丫丫
polybar需要从aur软件源安装，看文档补全依赖。也可以从archlinuxcn源安装这样更简单

### 三、美化和完善系统
美化所需软件
```
nerd-fonts-complete oh-my-zsh awesome-terminal-fonts 
```

下载并导入配置文件，配置文件位置一般都位*~/.config/* 文件夹内

完善系统

```
浏览器：firefox chrome
音乐播放器：netease-cloud-music
视频播放器：vlc
文件管理器：thunar
aur管理软件：yay
```

