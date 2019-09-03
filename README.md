subnodes (nextcloudpi adaptation)
=================

![](https://david-dm.org/chootka/subnodes.svg)

Subnodes is an open source project that turns your Linux device running the latest Raspbian release (as of this writing, Stretch Lite) into an offline mesh node and wireless access point.

This project is an initiative focused on streamlining the process of setting up a Raspberry Pi as a wireless access point for distributing content, media, and shared digital experiences. The device becomes a web server, creating its own local area network, and does not connect with the internet. This is key for the sake of offering a space where people can communicate anonymously and freely, as well as maximizing the portability of the network (no dependibility on an internet connection means the device can be taken and remain active anywhere). 

The device can also be configured as a BATMAN Advanced mesh node, enabling it to join with other nearby BATMAN nodes into a greater mesh network, extending the access point range and making it possible to exchange information with each other. Support for Subnodes has been provided by Eyebeam. This code is published under the [AGPLv3](http://www.gnu.org/licenses/agpl-3.0.html).

How to Install
--------------
Assuming you are starting with a fresh [Raspbian Stretch Lite](http://www.raspberrypi.org/downloads/) (Latest tested version: November 2018) installed on your SD card, these are the steps for setting up subnodes on your Raspberry Pi. It is also assumed that you have two wireless USB adapters attached to your RPi. They both must be running the nl80211 driver. [This guide](https://github.com/phillymesh/802.11s-adapters/blob/master/README.md) will help you find a suitable radio. If you are running a Raspberry Pi 3 or Pi Zero W, you only need one additional radio for the mesh point. The access point will be set up utilizing the Pi's internal wireless radio.

Also, if this is your first time connecting to your Raspberry Pi headlessly (i.e. via SSH), you must first enable SSH by placing an empty file with no filename extension simple called `ssh` in the root of your SD card.

* write NextCloudPI imae to sdcard

        https://ownyourbits.com/downloads/NextCloudPi_RPi_07-20-19/

* set up your Raspberry Pi with a basic configuration

        sudo raspi-config

* set up NextcloudPI to your liking

        https://docs.nextcloudpi.com/en/how-to-configure-nextcloudpi

* update apt-get

        sudo apt-get update

* clone the repository into your home folder (assuming /home/pi)

        mkdir subnodes; cd subnodes
        git clone [this repo] .

* configure your wireless access point and mesh network in subnodes.config in any text editor, or in the command line you can use nano

        nano subnodes.config

* run the installation script

        sudo ./install.sh

The installation process takes about 15 minutes. After it has completed, you will have a running lighttpd php7 web server, wireless access point, and BATMAN Advanced mesh node. Connecting to the network and navigating to a browser page will redirect you to your new captive portal page. It's only going to be a boilerplate (aka, default) lighttpd web page, so head into /var/www/html and create a new index.html file and go nuts.

From here, fork, build, share your ideas, and have fun!

references
----------
* [subnodes website](http://www.subnodes.org/)
* [Raspberry Pi](http://www.raspberrypi.org/)
* [eyebeam](http://eyebeam.org/)
