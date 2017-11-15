# Pi-Bluetooth-PS3

sudo apt-get install bluetooth  
sudo apt-get install bluetooth bluez-utils bluez-compat bluez-hcidump  
sudo apt-get install libusb-dev  
sudo apt-get install libbluetooth-dev  
/etc/init.d/bluetooth status  
  
cd  
mkdir sixpair  
cd sixpair  
wget "http://www.pabr.org/sixlinux/sixpair.c" -O sixpair.c
gcc -o sixpair sixpair.c -lusb  
sudo ./sixpair

Current Bluetooth master: xx:xx:xx:xx:xx:xx
Setting master bd_addr to xx:xx:xx:xx:xx:xx

cd
wget "https://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.1/QtSixA-1.5.1-src.tar.gz/download" -O QtSixA-src.tar.gz
tar -xvf QtSixA-1.5.1-src.tar.gz  
cd QtSixA-1.5.1/sixad  
make  
sudo make install  
  
cd  
git clone https://github.com/dusty-nv/turbo2.git  
cd turbo2  
cd sixad  
make  
sudo make install  
sudo sixad -start &  
sixad-bin[xxxx]: sixad started, long press the PS button now  
  
/usr/bin/sixad --stop  
