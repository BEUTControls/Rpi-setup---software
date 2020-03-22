# Rpi-setup-software
# This is to start from scratch to get the Raspberry pi talking.

SD card format software - https://www.sdcard.org/downloads/formatter/eula_windows/index.html

Format the card using SD card format software. Right clicking on SD card and format is just going to cause you problems.

Download Raspian Buster with desktop - https://downloads.raspberrypi.org/raspbian_latest

Start BelenaEtcher software or get Software download to burn image to SD - https://www.balena.io/etcher/

Burn image - open balenaEtcher - select the downloaded Raspian Image - Flash

Create 2 files and add to the SD card
Both of the files can be created with notepad. Setup the folder so it shows file extensions. Remove the .txt
1 - ssh - Note this should be an empty file and should not have .txt on the file.
2 - wpa_supplicant.conf
    file should contain
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=US

network={
	ssid="NETWORK NAME"
	psk="NETWORK PASSWORD"
	key_mgmt=WPA-PSK
}
Enter your Wifi name and password in ssid, and psk

Copy these files to the root directory of the SD card you just burned.
Eject the SD card and install in the Raspberry pi.
Power up the raspberry pi and find it on the network.
  I use an app on the phone (Net Analyzer) to find network devices

Connect to the raspberry pi (Window 10)
start CMD
in promt type: ssh pi@IP ADDRESS 
  example ssh pi@10.0.0.168
Enter password for pi: defualt password is raspberry

Get updates
sudo apt-get update

Install updates
sudo apt-get upgrade

type sudo raspi-config 
This will get you into configuration system
1: Change password
  You will be asked to enter new password twice
4 Localisation Options
  Here you can set the WIFI country and the timezone
5 Interfacing Options
  Enable VNC
  Enable I2C
  Enable 
  
Exit out of raspi-config
sudo reboot


You are done.

