# 系统下载
- [Kubuntu](https://kubuntu.org/getkubuntu/)  
- [北京外国语大学开源软件镜像站](https://mirrors.bfsu.edu.cn/ubuntu-cdimage/kubuntu/releases/)  
- [Microsoft Windows 10](https://www.microsoft.com/en-us/software-download/windows10ISO)
- [Microsoft Windows 11](https://www.microsoft.com/en-us/software-download/windows11)
- [rufus](https://rufus.ie/)  
- [balenaEtcher](https://www.balena.io/etcher/)  
- [微 PE 工具箱](https://www.wepe.com.cn/download.html) 

# 设置系统关机的最长等待时间
在 `/etc/systemd/system.conf` 的末尾加上：   
```
DefaultTimeoutStartSec=10s
DefaultTimeoutStopSec=10s
```

# 禁用睡眠、休眠功能
```bash
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

# 修改 grub 启动的等待时间
在 `/etc/default/grub` 加上一行  
```
GRUB_RECORDFAIL_TIMEOUT=1
```
接下来执行：  
```bash
sudo update-grub
```

# 杂
```bash
sudo apt install fcitx-pinyin git flameshot # 拼音、截图和 git
sudo apt install handbrake  # 音视频转码ui
sudo apt remove plasma-discover # 移除 KDE 自带的应用商店
sudo apt remove okular    # 移除 Okular 文档查看器
sudo snap install powershell --classic
sudo snap install libreoffice

flameshot gui # flameshot 的直接截图指令
./xx.AppImage --appimage-extract  # 解压 appImage 文件
```
- [Lutris](https://github.com/lutris/lutris/releases)

# 设置输入法以及系统代理变量
在 `/etc/environment` 的末尾加上：   
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
INPUT_METHOD=fcitx
SDL_IM_MODULE=fcitx
GLFW_IM_MODULE=ibus
https_proxy=http://127.0.0.1:1082
http_proxy=http://127.0.0.1:1082
all_proxy=socks5://127.0.0.1:1082
```

# KVM 虚拟机和 remmina 
```bash
sudo apt install virt-manager qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils remmina
sudo systemctl enable libvirtd.service
sudo systemctl restart libvirtd.service
sudo virt-manager && nohup remmina
```

# node 和 Typescript
- [node 官网](https://nodejs.org/en/download/) 
```bash
sudo snap install node --classic
sudo npm config set registry https://registry.npmmirror.com
sudo npm install -g typescript
```

# 各种软件
- [VSCodium](https://github.com/VSCodium/vscodium/releases) ，我的同步扩展：`zokugun.sync-settings`   
- [Mega](https://mega.io/desktop)  ，删除它的apt包源： `sudo rm "/etc/apt/sources.list.d/megasync.list"`
- [Firefox ESR](https://www.mozilla.org/en-US/firefox/all/#product-desktop-esr)  ，设置为系统默认浏览器时，后续参数要加上 `%u`
- [Telegram](https://desktop.telegram.org/)
- [Steam](https://store.steampowered.com/about/)
- [Discord](https://discord.com/)
- [Hello Minecraft Launcher](https://github.com/huanghongxun/HMCL/releases)
- [RustDesk](https://github.com/rustdesk/rustdesk/releases)

# Windows Only
- [steamcommunity 302](https://www.dogfight360.com/blog/686/)
- [Steam下载CDN重定向](https://www.dogfight360.com/blog/1531/)
- [Dism++](https://github.com/Chuyu-Team/Dism-Multi-language/releases)
- [7-Zip](https://www.7-zip.org/download.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Microsoft Build of OpenJDK](https://docs.microsoft.com/en-us/java/openjdk/download)
- [Oracle Java](https://java.com/zh-CN/download/manual.jsp)
- [Microsoft Visual C++ Redistributable](https://docs.microsoft.com/en-US/cpp/windows/latest-supported-vc-redist?view=msvc-170)
- [Git](https://git-scm.com/downloads)
- [PowerShell](https://github.com/PowerShell/PowerShell#get-powershell) 
- [Visual Studio](https://visualstudio.microsoft.com/)
- [Visual Studio 2019](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=16)
- [HxD](https://mh-nexus.de/en/downloads.php?product=HxD20)
- [Vegas 官方的下载直链收集](https://www.vegascreativesoftware.info/us/forum/faq-where-can-i-download-vegas-pro-and-other-vegas-software--104782/)
- [Vegas Pro 15](http://dl04.magix.net/2017/VEGASPro15/update/VEGAS_Pro_15.0.0.416_DE-EN-FR-ES_x64.exe)
- [K-Lite Codec Pack](https://codecguide.com/download_kl.htm)
- [CloudMoe Windows 10+ Activation Toolkit Digital Edition](https://github.com/TGSAN/CMWTAT_Digital_Edition/releases)


# go
[官网下载](https://go.dev/dl/) ，解压到 `/usr/local/`   
在 `$HOME/.profile` 里面写上：  
```bash
export PATH=$PATH:/usr/local/go/bin
export GOROOT=/usr/local/go
```
更换国内源，关闭默认的 CGO ：   
```bash
go env -w GO111MODULE="on"
go env -w GOPROXY="https://goproxy.cn,direct"
go env -w CGO_ENABLED="0"
```
