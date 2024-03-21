---
{}
---

Title: Using Docker on 18.04 Beta
Date: 2018-03-08 13:00
Category: coding

If you have tried to install docker via the usual
[instructions](https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository),
you will find that they've not pushed packages for Ubuntu 18.04 "Bionic Beaver" yet:

```shell
$ sudo apt install docker-ce
[...]
E: Unable to locate package docker-ce
```
This is understandable, as the release day isn't for a month. But what if you're a bleeding-edge adopter, such as myself? It's dead easy:

Just edit `/etc/apt/sources.list` and change the line from:

```shell
deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
```
to

```shell
deb [arch=amd64] https://download.docker.com/linux/ubuntu artful stable
```

Your install will now work. Just remember to update it once docker start releasing official packages. Remember, this likely isn't supported, so YMMV.
