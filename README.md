# gentoo-install-guide

## Introduction

Welcome to this wonderful Gentoo Install Guide. This allows you the ability 
to successfully install Gentoo properly....

## Preparing

Later on...

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



## How to install xorg-drivers

In this section, we are going to install xorg-drivers in Gentoo. To have a graphical interface at least...





## Portage Reference Guide

In this section, this talks about some about the tips and tricks on Portage.
