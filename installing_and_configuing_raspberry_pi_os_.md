# Installing and Configuring Raspberry PI OS Before Booting
(This guide is for Raspberry Pi OS)

1. Download Raspberyr PI OS from https://www.raspberrypi.org/downloads/raspberry-pi-os/
2. Unzip the image: `unzip 2020-05-27-raspios-buster-lite-armhf.zip`
3. Insert the SD card and find it's identifier using `lsblk` (it'll probably be called `mmcblk0` on an OS like Ubuntu/Debian)
4. Burn the disk image to the SD Card: `sudo dd bs=4M if=2020-05-27-raspios-buster-lite-armhf.img of=/dev/mmcblk0 conv=fsync` - be sure to replace /dev/mmcblk0 with the device name you found in step 3.
5. Wait for a few minutes, and the image should be burned to the SD Card

## Enabling SSH
You can enable SSH before you insert the SD card to the raspberry pi 

1. Insert the SD card into your PC/Laptop/Mac
2. Find where it mounts the SD Card to (in Ubuntu/Debian Linux, it's probably `/media/<your username>/boot`)
3. Create an empty file called `ssh` in this directory. `touch /media/<your username>/boot/ssh`

## Configuring WiFi
You can configure WiFi before you insert the SD card to the raspberry pi 

1. Insert the SD card into your PC/Laptop/Mac
2. Find where it mounts the SD Card to (in Ubuntu/Debian Linux, it's probably `/media/<your username>/boot`)
3. Create a file in this directory called `wpa_supplicant.conf`. The file should contain the following details:

```
country=GB # Your 2-digit country code
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
network={
    ssid="YOUR_NETWORK_NAME"
    psk="YOUR_PASSWORD"
    key_mgmt=WPA-PSK
}
```
