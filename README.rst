About
=====

OpenWrt feed to integrate the Linux kernel version of kodo, fifi and
kodo-network in the firmware images.

Requirements
------------

* OpenWrt
* Git

How to compile the module
-------------------------

Download a current version of OpenWrt, add the feed at the end of
feeds.conf.default, refresh the local feed database and add the modules to the
available packages::

    echo 'src-git kodo https://github.com/steinwurf/kodo-kernel-openwrt-feed.git' >> feeds.conf.default
    ./scripts/feeds update
    ./scripts/feeds install kmod-kfifi kmod-kodo kmod-kodo-network

Enabling the modules
--------------------

The modules can be enabled using menuconfig::

    make menuconfig
    --> Kernel modules
        --> Libraries
            <*> kmod-kfifi
            <*> kmod-kodo
        --> Network Support
            <*> kmod-kodo-network
