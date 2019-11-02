+++
title = "SSH (mosh) to Raspberry Pi using iPad Pro over USB-C"
date = "2019-11-02T18:07:37+07:00"
draft = true
categories = []
+++

I love my 11” iPad Pro. IMO, it's the best device Apple's ever made. With its USB-C port, now we can connect an iPad to a Raspberry Pi for a fully immersive Linux development environment. This article will document the process of setting things up. 

## Setup Raspbian with SSH and Ethernet over USB

- Head over to [https://www.raspberrypi.org/downloads/raspbian/](https://www.raspberrypi.org/downloads/raspbian/) to download your choice of image. 
- "Burn" the image to a micro SD card
```bash
diskutil list # make note of where the SD card is mounted

# replace rdiskN with the appropriate value
sudo dd bs=1m if=2019-09-26-raspbian-buster-lite.img of=/dev/rdiskN conv=sync
```
- Enable SSH 
```bash
touch /Volumes/boot/ssh
```
- Add `modules-load=dwc2,g_ether` to `cmdline.txt` after `rootwait` and append `dtoverlay=dwc2` to `config.txt`

```bash
sed -i '' 's/rootwait/rootwait modules-load=dwc2,g_ether/' /Volumes/boot/cmdline.txt
echo 'dtoverlay=dwc2' >> /Volumes/boot/config.txt
```

## Connect Pi to the iPad

Now you can connect the Pi to your iPad Pro using USB-C to micro USB cable, or using a dongle. The Pi draws power and connect to the iPad using a single cable 💯.

The first boot is going to take couple minutes since the Pi needs to expand its file system. After that you should be able to SSH to the Pi under `raspberrypi.local`

If you don't know what SSH client to use on iOS, I highly recommend [Blink](https://www.blink.sh/).

![Raspberry Pi tethered iPad](/images/raspberrypi-ipad.jpg)

Voila! Now that you have a shell, you can do anything :).

## Setup mosh and tmux 

Now that we've got SSH up and running, it's always a good idea to add `mosh` and `tmux` to the stack. I won't go into details on how to set them up since there are plenty of good resources on the Internet for it. But the ability to connect the iPad to a Pi and resume your work session feels absolutely magical 🧙‍♂️.
