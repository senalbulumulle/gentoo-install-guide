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


Here is how you are able to add packages to `ACCEPT_KEYWORDS`
