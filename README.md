# Pi-Bluetooth-PS3


lsusb|grep Sony  1
\# Bus 001 Device 008: ID 054c:0268 Sony Corp. Batoh Device / PlayStation 3 Controller   
  
sudo vi /etc/udev/rules.d/90-joystick.rules  
ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0268", MODE="0660", GROUP="joystick"  
\# Vender "054c" = "SONY" , Product "0268" = "Sony PLAYSTATION(R)3 Controller"  
  
sudo groupadd -r joystick  
sudo usermod -a -G joystick pi  
sudo udevadm control --reload-rules  
  
reboot  
  
Press the center of the PS button  
Glowing only LED1  
  
apt-get install jstest-gtk  
jstest-gtk  
  
   
sudo apt-get install bluetooth bluez-hcidump  
sudo apt-get install libusb-dev libbluetooth-dev  
sudo /etc/init.d/bluetooth start  
/etc/init.d/bluetooth status  
lsusb|grep Sony
  
cd  
mkdir sixpair  
cd sixpair  
wget "http://www.pabr.org/sixlinux/sixpair.c" -O sixpair.c  
gcc -o sixpair sixpair.c -lusb  

--Connect the USB cable from the PlayStation controller  
sudo ./sixpair

Current Bluetooth master: xx:xx:xx:xx:xx:xx  
Setting master bd_addr to xx:xx:xx:xx:xx:xx  
  
--cd  
--wget "https://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.1/QtSixA-1.5.1-src.tar.gz/download" -O QtSixA-src.tar.gz  
--tar -xvf QtSixA-1.5.1-src.tar.gz  
--cd QtSixA-1.5.1/sixad  
--make  
--sudo make install  
  
cd  
git clone https://github.com/dusty-nv/turbo2.git  
cd turbo2  
cd sixad  
make  
sudo make install  
sudo sixad -start &  
--Disconnect the USB cable from the PlayStation controller

sixad-bin[xxxx]: sixad started, long press the PS button now  
sixad-sixaxis[xxxx]: started
sixad-sixaxis[xxxx]: Connected 'PLAYSTATION(R)3 Controller (xx:xx:xx:xx:xx:xx)' [Battery xx]  
  
sudo apt-get install jstest-gtk  
jstest-gtk  
   
/usr/bin/sixad --stop  
/usr/bin/sixad --start &  

https://www.raspberrypi.org/forums/viewtopic.php?t=140515  

sudo vi ~/.config/autostart/ps3.desktop

[Desktop Entry]  
Encoding=UTF-8  
Type=Application  
Name=PS3  
Comment=  
Exec=sixad --start  
StartupNotify=false  
Terminal=false  
Hidden=false  

sudo chmod a+r ~/.config/autostart/ps3.desktop

https://qiita.com/KurokoSin/items/f0f2de392d52821e7fa6

https://qiita.com/shskwmt/items/fffabf521201f5835214

sudo apt-get install bluez bluez-utils  
sudo systemctl start bluetooth.service  
sudo systemctl enable bluetooth.service  

bluetoothctl  
devices  
scan on  
pair    MACADDRESS  
trust   MACADDRESS  
connect MACADDRESS  
exit  

more /etc/udev/rules.d/10-local.rules  
vi   /etc/udev/rules.d/10-local.rules  
ACTION=="add", KERNEL=="hci0", RUN+="/usr/bin/hciconfig hci0 up"  

https://qiita.com/propella/items/6daf3c56e26f709b4141
