# raspberrypi
### Download and unarchive openvswitch:
wget http://openvswitch.org/releases/openvswitch-2.5.2.tar.gz
tar -xvzf openvswitch-2.5.2.tar.gz
cd openvswitch-2.5.2

### Install all dependencies:
sudo apt-get install python-simplejson python-qt4 libssl-dev python-twisted-conch automake autoconf gcc uml-utilities libtool build-essential pkg-config

### Build openvswitch:
./configure
make -j4
make -j4 install

### Set up local variables:
cd datapath/linux/
modprobe openvswitch
cd ../..
touch /usr/local/etc/ovs-vswitchd.conf
mkdir -p /usr/local/etc/openvswitch
ovsdb-tool create /usr/local/etc/openvswitch/conf.db vswitchd/vswitch.ovsschema


### Create starting file:
sudo nano /etc/init.d/superscript
"""
#!/bin/bash

ovsdb-server    --remote=punix:/usr/local/var/run/openvswitch/db.sock \
                --remote=db:Open_vSwitch,Open_vSwitch,manager_options \
                --private-key=db:Open_vSwitch,SSL,private_key \
                --certificate=db:Open_vSwitch,SSL,certificate \
                --bootstrap-ca-cert=db:Open_vSwitch,SSL,ca_cert \
                --pidfile --detach
ovs-vsctl --no-wait init
ovs-vswitchd --pidfile --detach
"""


### Start openvswitch service:
/etc/init.d/superscript


### Set up starting openvswitch on boot:
/etc/init.d/superscript
sudo chmod 755 /etc/init.d/superscript
sudo update-rc.d superscript defaults
