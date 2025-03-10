subnodes (NextCloudPI adaptation)
=================

![](https://david-dm.org/chootka/subnodes.svg)

Subnodes is an open source project that turns your Linux device running the latest Raspbian release (as of this writing, Stretch Lite) into an offline mesh node and wireless access point.

This project is an initiative focused on streamlining the process of setting up a Raspberry Pi as a wireless access point for distributing content, media, and shared digital experiences. The device becomes a web server, creating its own local area network, and does not connect with the internet. This is key for the sake of offering a space where people can communicate anonymously and freely, as well as maximizing the portability of the network (no dependibility on an internet connection means the device can be taken and remain active anywhere). 

Support for Subnodes has been provided by Eyebeam. This code is published under the [AGPLv3](http://www.gnu.org/licenses/agpl-3.0.html).

How to Install
--------------
Note: If this is your first time connecting to your Raspberry Pi headlessly (i.e. via SSH), you must first enable SSH by placing an empty file with no filename extension simple called `ssh` in the root of your SD card. Also, the access point will be set up utilizing the Pi's internal wireless radio.

* download NextCloudPI image

        https://ownyourbits.com/downloads/NextCloudPi_RPi_07-20-19/

* write image to SDcard

        sudo dd if=NextCloudPi_RPi_07-20-19.img of=/dev/sd[x] bs=1M
        
* add file named 'ssh' to boot partition of SDcard

        right-click, 'new file' -> 'ssh' (no extensions)

* put SDcard into your RPi, and power it on

* connect RPi using Ethernet to your laptop and enable bridging or internet-sharing between your wireless and ethernet connections

* ssh to your RPi

         ssh pi@nextcloudpi.local
         (password: raspberry)

* set up your Raspberry Pi with a basic configuration

        sudo ncp-config
                (Say 'No' at update prompt)
                CONFIG -> nc-httpsonly -> no
                
* wait about 5 minutes until green activity LED stops glowing (system auto-update)

        # run top to see what's happening
        top

* clone the repository into your home folder (assuming /home/pi)

        git clone https://github.com/k0a1a/subnodes-nextcloudpi.git  
        cd subnodes-nextcloudpi

* configure your wireless access point in subnodes.config in any text editor, or in the command line you can use nano

        nano subnodes.config

* run the installation script

        sudo ./install.sh

The installation process takes about 5 minutes. After it has completed, you will have a running NextCloud instance and a wireless access point. Connect to http://nextcloudpi.local to activate your instalnce!

## extra

### use Pagekite.com service to make your instalnce available over the Internet

* install pagekite package

         sudo apt-get install pagekite

* sign-up with pagekite service

         sudo pagekite --signup --savefile /etc/pagekite.d/99_nextcloud

* configure pagekite

         sudo pagekite [name-for-your-site].pagekite.com --savefile /etc/pagekite.d/99_nextcloud
         
* restart pagekite

         sudo service pagekite restart
         


references
----------
* [subnodes website](http://www.subnodes.org/)
* [NextCloudPi configuration](https://docs.nextcloudpi.com/en/how-to-configure-nextcloudpi)
* [NextCloudPi website](https://nextcloudpi.com)
* [Raspberry Pi](http://www.raspberrypi.org/)
* [eyebeam](http://eyebeam.org/)
