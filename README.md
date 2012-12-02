smileplug-bsp
=============

This is a bunch of initial config.  This will include a set of configs to be applied in the BSP.

Pacman Package Manifest
=======================

* nodejs
* openssl
* make
* gcc
* sysstat (we just use sar)
* python
* python2-distribute
* python2-pyopenssl
* iperf

> pacman -S openssl gcc nodejs make

NPM Modules:

* forever (install in global)
* forever-webui (npm package is busted, use BETA, off HEAD of https://github.com/SMILEConsortium/forever-webui.git) ,
  wget https://nodeload.github.com/FGRibreau/forever-webui/tarball/master , install dependencies, access on port 8085

Other Non-NPM Node Software:
* SMILE Server 0.2.3 (this holds pointers to all Android software used)
* Plugmin Server 0.3.3

Scripts:
* dhcpd-status.sh -> /root/spdist/dhcpd-pool-0.2/dhcpd-status-arch.sh

General Config
==============

* Standard root password: root // XXX CHANGE ME
* .bashrc in /root is used
* set default root PATH to include ~/root/bin


Assigned Ports
==============

* 80 (SMILE and JS.js) - We really need to put all of this behind a reverse proxy
* 8008 (TTY.js)
* 8085 (forever-webui)
* 9023 (NIDE)
* 9080 (plugmin WS/Web UI)
* 5000 (epochedu) - 

Python Modules:

* curl -O http://python-distribute.org/distribute_setup.py
* sudo python distribute_setup.py
* sudo easy_install pip
* sudo pip install virtualenv
* sudo pip install virtualenvwrapper

Additional Software:

* virtualenv goenv
* . ./goenv/bin/activate

Users & Groups:

* Default Root and SUDO configuration, see: http://archlinuxarm.org/support/guides/system/first-steps
* No other non-default users

Added for testing:

* ntop
* afps-fs (may consider adding this to above list)

Some manual commands to run in the configuration of a new BSP based on arch:

* For UFW, open all connections from the associated networks for the administrative 
  network 10.0.0.0 and the default WIFI AP network 10.1.0.0
    # This generates the /usr/lib/ufw/user.conf commands used to store the rules
    ufw allow from 10.0.0.0/24
    ufw allow from 10.1.0.0/24
