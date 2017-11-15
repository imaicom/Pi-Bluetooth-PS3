# Pi-Bluetooth-PS3

sudo apt-get install bluetooth  
sudo apt-get install bluetooth bluez-utils bluez-compat bluez-hcidump  
sudo apt-get install libusb-dev  
sudo apt-get install libbluetooth-dev  
  
cd  
mkdir sixpair  
cd sixpair  
wget "http://www.pabr.org/sixlinux/sixpair.c" -O sixpair.c
gcc -o sixpair sixpair.c -lusb
