# DefCon31HRVPresentations
Presentations and their notes that I presented at the Ham Radio Village for DefCon 31

# Digital Modes Primer
This presentation goes over the most popular digital modes available for use by amateur radio operators. Includes audio samples of many.

# Ham digital modes without a Raspberry Pi
After the p4ndem1c, the raspberry pi became very challenging to obtain. This presentation goes over research I completed into alternative SBCs to the Raspberry Pi that can be used for ham radio digital modes.

# Notes for individual SBC models researched for this presentation
Below are random notes I wrote during my research. This includes many commands I used to get things to work. 

## Orange Pi 4 LTS notes

Choose Gnome Desktop flavor of Armbian for Orange Pi 4 LTS

RealVNC is not installed in Armbian by default.

Commands to run before installing:

```
sudo apt-get install libraspberrypi0
sudo ln -fs /usr/lib/aarch64-linux-gnu/libbcm_host.so /usr/lib/libbcm_host.so.0 
sudo ln -fs /usr/lib/aarch64-linux-gnu/libvcos.so /usr/lib/libvcos.so.0
sudo ln -fs /usr/lib/aarch64-linux-gnu/libvchiq_arm.so /usr/lib/libvchiq_arm.so.0
sudo ldconfig
```

Link to RealVNC installer: https://downloads.realvnc.com/download/file/vnc.files/VNC-Connect-Installer-1.3.0-Linux-ARM64.tar.gz

Install gnome-classic if you want the menus

## Libre Renegade notes

Boots Libre’s Raspbian without any issues. 

No wifi. If you want WiFi, you need to add it. Attempting RTL8811AU USB wifi adapter.

Enable NetworkManager in raspi-config
Enable ssh

Connect to ethernet

Extra installed packages:
dkms
screen
tmux

apt-get update && apt-get dist-upgrade

Install Wifi USB driver

Follow instructions at: https://github.com/morrownr/8821au-20210708 

I opted for the AP mode driver settings when building the driver.

Reboot. Always reboot.

## Orange Pi 5B notes

Choose Armbian 23.5 Jammy Gnome if you want the stable release

To enable access to the emmc, replace fdtfile=rockchip/rk3588s-orangepi-5.dtb in /boot/armbianEnv.txt with fdtfile=rockchip/rk3588s-orangepi-5b.dtb
  - Windows will not recognize the vfat boot partition as it is labeled as a linux boot partition, not fat
  - You can either fiddle with the partition type using gedit or linux, or just mount the partition using a linux system (for example, on your first boot into armbian)

To make gnome look like what is more familiar:

```
sudo apt install lxdm gnome-system-tools
sudo apt remove nodm
sudo dpkg-reconfigure lxdm

sudo apt install lxde
sudo reboot
```

Choose the LXDE session to see a list of menus like what you expect

The date is set wrongideewrongwrong at the factory. This breaks apt with weird errors about the latest release not being valid yet

RealVNC is not installed in Armbian by default.

Commands to run before installing:

```
sudo apt-get install libraspberrypi0
sudo ln -fs /usr/lib/aarch64-linux-gnu/libbcm_host.so /usr/lib/libbcm_host.so.0 
sudo ln -fs /usr/lib/aarch64-linux-gnu/libvcos.so /usr/lib/libvcos.so.0
sudo ln -fs /usr/lib/aarch64-linux-gnu/libvchiq_arm.so /usr/lib/libvchiq_arm.so.0
sudo ldconfig
```

Link to RealVNC installer: https://downloads.realvnc.com/download/file/vnc.files/VNC-Connect-Installer-1.3.0-Linux-ARM64.tar.gz

# Build-a-pi
Use git to clone KM4ACK’s build-a-pi tool: 
```
git clone https://github.com/km4ack/pi-build.git
```

Launch the script with this command:
```
./pi-build/build-a-pi
```

## Packages I typically install using the script
This is the very base minimal list of ham apps that I always use. Feel free to install everything, it will just take longer.

- HAMLIB
- DIREWOLF
- AX25
- PULSE
- CHIRP
- JS8CALL
- WSJTX
- QSSTV
- GRIDTRACKER
- TQSL
