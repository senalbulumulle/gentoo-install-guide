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

Then the first thing to do is to use this command:

```shell
emerge-webrsync
```

Then you need to use this command: 

```shell
emerge --sync
```

Then you need to use this command. This allows the ability to select the profile. Then you need to select the desktop profile... or you can keep it the default one...

```shell
eselect profile list 
```

Then you need to have the ability to update the world set.

```shell
emerge avuNDa @world
```

> Warning: You can also use the post install too as reference as well. 



## Updating Portage:

In this section, we are going to be talking about how to update the portage package manager. 

## Post Install (After Install)

In this section, we are going to talk about setting up stuff in the post installation of Gentoo...

The first thing you need to do is to initialize emerge to sync the repositories: 

```shell
emerge --sync
```

```shell
emerge @world
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

# 

## Portage Reference Guide

In this section, this talks about some about the tips and tricks on Portage.
