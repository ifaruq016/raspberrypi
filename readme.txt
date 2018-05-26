## Install Iperf 3.1.3 via command line :
# Ubuntu 64 bits, Debian 64 bits, Mint 64 bits
# AMD64

me@ubuntu~$ sudo apt-get update
me@ubuntu~$ sudo apt-get upgrade

# Download iperf3 file.
me@ubuntu~$ wget https://iperf.fr/download/ubuntu/libiperf0_3.1.3-1_amd64.deb
me@ubuntu~$ wget https://iperf.fr/download/ubuntu/iperf3_3.1.3-1_amd64.deb

# Installing
me@ubuntu~$ sudo dpkg -i libiperf0_3.1.3-1_amd64.deb iperf3_3.1.3-1_amd64.deb

--------------------------------------------------------------------------------------------------------
