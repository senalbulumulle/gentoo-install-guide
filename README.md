# gentoo-install-guide

## Introduction


## Preparing

Later on...


## Post Install
In this section, we are going to talk about setting up 
stuff in the post installation of Gentoo...

The first thing you need to do is to initialize emerge
to sync the repositories: 

```shell
emerge --sync
```

Also the most important thing is to also update all 
the packages. (Depends...). Don't use this command..
unless you are ready to make Gentoo to take it's 
own time to compile and update all the packages. 

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
