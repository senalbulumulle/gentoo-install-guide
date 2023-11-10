# gentoo-install-guide

## Introduction

Welcome to this wonderful Gentoo Install Guide. This allows you the ability 
to successfully install Gentoo properly....

## Preparation

In this section, we are going to show you how to use disk preparations before you are able to install Gentoo.

#### Partitioning the disks

I recommend you to use `cfdisk` to partition the disks before installing Gentoo... because it is much easier. 

#### Creating the file systems

```shell
mkfs.vfat -F 32 /dev/vda1
```

```shell
mkswap /dev/sda2
```

```shell
mkfs.ext4 /dev/vda3
```

#### Downloading the Gentoo tarball

Before doing that, the first thing you need to do  is to create a directory inside `/mnt`

`mkdir --parents /mnt/gentoo`

Then the second thing to do is to mount the drive to `/mnt/gentoo`

`mount /dev/sda3 /mnt/gentoo`

Then the third thing to do is to enable permissions for the directory

`chmod 1777 /mnt/gentoo/tmp`



Then you need to download the tarball

```shell
wget https://distfiles.gentoo.org/releases/amd64/autobuilds/20231105T170200Z/stage3-amd64-openrc-20231105T170200Z.tar.xz`
```



Then you need to unzip the tarball

```shell
tar xpvf stage3-*.tar.xz --xattrs-include='*.*' --numeric-owner
```



Then you need to need to do is to put this command: 

```shell
arch-chroot /mnt/gentoo
```

## Post Install

In this section, we are going to talk about setting up stuff in the post installation of Gentoo...

The first thing you need to do is to initialize emerge to sync the repositories: 

```shell
emerge --sync
```

```shell
emerge @world
```

Here is how you are able to add packages to `ACCEPT_KEYWORDS`.
Here is just an example...

```shell
echo "www-client/firefox-bin ~amd64" >> /etc/portage/package.accept_keywords/firefox-bin
```

This is where we are able to accept keywords for `xorg`.

```shell
echo "x11-base/xorg-apps ~amd64" >> /etc/portage/package.accept_keywords/xorg-apps
```

This is how you are able to edit the `/var/lib/portage/world` file: 

```shell
app-arch/zstd
app-portage/gentoolkit
dev-vcs/git
net-misc/dhcpcd
sys-boot/syslinux
sys-kernel/dracut
sys-kernel/gentoo-kernel-bin
sys-kernel/linux-firmware
```

## Adjusting stuff in the `make.conf` file

In this section, we are going to be talking about how to adjust settings in the `/etc/portage/make.conf ` file. The first thing you need to do is to use `nano` and then point it to the `/etc/portage/make.conf` file. Once you have done that you need to add these syntaxes into the file... displayed here....

```shell
ACCEPT_KEYWWORDS="~amd64"
USE="networkmanager bluetooth pipewire plymouth branding elogind dbus X"
ACCEPT_LICENSE="* @EULA"
FEATURES="parallel-fetch parallel-install candy"
MAKEOPTS="-j6 -l6"
EMERGE_DEFAULT_OPTS="--ask --verbose --load-average=6 --jobs=6"
```

## How to adjust font size in the tty

In this section we are going to be talking about how to adjust font size in Gentoo...

The first thing to do is to put this command in before doing the next step. This particular command allows the ability to adjust the font size in the TTY.  

```shell
emerge terminus-font && emerge -avuNDa @world
```

Then the next thing to do is to use this to adjust the font in the tty

```shell
setfont ter-v24b
```

## How to install xorg

In this section, we are going to install xorg in Gentoo. To have a graphical interface at least...

Here are the USE-Flags

```shell
-debug
+elogind
-minimal
-suid
-systemd
-test
+udev
-unwind
-xcsecurity
-xephyr
-xnest
+xorg
-xvfb
```

```shell
emerge elogind  && emerge xorg-drivers && emerge -avuNDa @world
```

```shell
emerge xf86-video-intel && emerge avuNDa @world
```

```shell
emerge xclock && emerge avuNDa @world
```

```shell
emerge xorg- && emerge avuNDa @world
```

## How to install eix

In this section, we are going to install eix in Gentoo. To make it easier... at least.

```shell
emerge eix && emerge -avuNDa @world
```

## Portage Reference Guide

In this section, this talks about some about the tips and tricks on Portage.
