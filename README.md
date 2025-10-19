# My Archlinux Experince ~cn~
I am a firsthand, This article may full mistakes

## Insatll Archlinux
I recommand use [Ventoy](https://www.ventoy.net/cn/index.html) or [Refus](https://rufus.ie/zh/). *Former*: you can only drag the ISO file into USB flash divice, and it will be a Startup Disk. You also save other files with ISO files. It's okay. *Latter*: the whole U will be a Startup Disk.

#### Thought using command way install Arch, you get know Archinstall 
Before using Archinstall, you need connect Internet (this command also used to install in command way)
**`$ iwctl`** $~~~$ [iwctl](https://wiki.archlinux.org/title/Iwd)
Then use **`archinstall`** , For Chinese mainland, you need **proxy**
Other steps you can learn by Internet

**Attention:** make sure you already add **user** successfully , and **==Confirm it==**
If you not succeed make a user,
- [ ] solution  #TODO

## Log in Archlinux
#### Add Archlinx CN Package Mirror
- [Official Repository Address](https://repo.archlinuxcn.org)
[Tsinghua mirror](https://mirrors.tuna.tsinghua.edu.cn/help/archlinuxcn/ "the archlinuxcn package mirror")
Add Tsinghua mirror
 Usage: add the following two lines at the end of the **`/etc/pacman.conf`**
```
[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
Other mirrors
```
# Ustc
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
# Ali
Server = https://mirrors.aliyun.com/archlinuxcn/$arch
```
then use command install **`archlinuxcn-keyring`** to input GPG key
```
$ sudo pacman -Sy archlinuxcn-keyring
```
#### Install yay
If you input archlinuxcn mirror, you can directly use **`pacman`** to install

```
$ sudo pacman -S yay
```
Not ?
> I learned form **BV1Rs421K7NS**

use **`git`** to install **`yay`**
```
$ sudo pacman -S git  //If you not install git
$ sudo pacman -S base-devel
$ git clone https://aur.archlinux.org/yay.git
$ sudo chown -R 用户名:users ./yay  // grant the user permission to modify this file
$ cd yay
$ makepkg -si
```
*If you don't use **`proxy`** , you may **stuck***
#When you are stucking, press **`ctrl+c`** to stop the process
#Input following command
```
$ go env -w GO111MODULE=on
$ go env -w GOPROXY=https://goproxy.cn,direct
$ export GO111MODULE=on
$ export GOPROXY=https://goproxy.cn
$ makepkg -si
``` 
then you can install **`yay`**

#### Install chines fonts
> **BV1jys6eaEtM**

Using following command install **chinese fonts**
```
$ sudo pacman -S noto-fonts noto-fonts-cjk noto-fonts-extra noto-fonts-emoji ttf-dejavu ttf-liberation
```
```
$ sudo nano /etc/locale.gen
```
remove sign **`#`** before
**`zh_CN.UTF-8 UTF-8`**
then 
```
$ su
# locale-gen && echo 'LANG=zh_CN.UTF-8' > /etc/locale.conf
```
change the system language in settings

#### Install fcitx5
> **BV1jys6eaEtM**

```
$ sudo pacman -S fcitx5-im fcitx5-rime
```

```
$ cd ~/.local/share/fcitx5/rime
$ git clone https://github.com/iDvel/rime-ice.git // a theme
$ cp -r ./rime-ice/* .
```
reboot fcitx5 

**==I think the bascial settings already setting==**
