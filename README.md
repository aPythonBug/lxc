# Install lxc on ubuntu 16.04

    $ sudo sh -c "apt update && apt upgrade -y"  - Fetches the list of available updates and strictly upgrades the current packages
    $ sudo apt install -y lxd zfsutils-linux     - Install lxc/lxd and fzsutils-linux packages

# add user to the LXD group for management purpose
    $ sudo adduser {yourUserName} lxd
    $ newgrp lxd

# Configure LXD storage and networking option
    $ sudo lxd init
    
# Creating your first Linux container

a) To list all images:

    $ lxc image list images:
    $ lxc image list images: | grep -i centos
    $ lxc image list images: | grep -i ubuntu
    $ lxc image list images: | grep -i debian
    
b) To create and start containers from images use the launch command:
    
    $ lxc launch images:{distro}/{version}/{arch} {containerName}
    
Ex:

    $ lxc launch images:alpine/3.8/amd64 alpine-c1
    $ lxc launch images:centos/7/amd64 cenots-c2
    $ lxc launch images:ubuntu/bionic/amd64 ubuntu-nginx-c3
    $ lxc launch images:debian/stretch/amd64 debian9-c4
    
c) List the existing containers:

    $ lxc list --fast
    $ lxc list | grep RUNNING
    $ lxc list | grep STOPPED
    $ lxc list | grep
    $ lxc list "*c1*"
    $ lxc list "*c2*"
    $ lxc list
    
d) To gain login and gain shell access in a container named file-server , enter:

    $ lxc exec debian9-c4 bash
    
    
e) Start containers using the following cli:

    $ lxc start {containerName}
    $ lsc start cenots-c2 opensuse-stable-c8

f) Stop containers using the following syntax:

    $ lxc stop {containerName}
    $ lsc stop cenots-c2 opensuse-stable-c8

g) Want to restart your containers for any reasons? Try:

    $ lxc restart {containerName}
    $ lsc restart cenots-c2 opensuse-stable-c8


h) Deleting containers:

    $ lxc delete {containerName}
    $ lxc delete cenots-c2

You may get the following error while deleting the container:

    The container is currently running, stop it first or pass –force.

To fix this:

    $ lxc stop {containerName} && lxc delete {containerName}
    
i)  Show information on LXD servers and containers with following command:

    $ lxc info
    $ lxc info {containerName}   
 
