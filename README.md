# ChickenCam

![](/server/static/img/chicken.jpg)

## Requirements

- [Raspberry Pi](https://www.amazon.com/Raspberry-Pi-RASP-PI-3-Model-Motherboard/dp/B01CD5VC92/ref=sr_1_4?s=pc&ie=UTF8&qid=1473017394&sr=1-4&keywords=raspberry+pi)
- [Camera without IR filter](https://www.amazon.com/gp/product/B00KX3HS4K/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1)
- [Weatherproof extension cord](https://www.amazon.com/gp/product/B00OS7ELK6/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1)
- [Infrared LEDs](https://www.amazon.com/gp/product/B00ULB0U44/ref=oh_aui_detailpage_o04_s00?ie=UTF8&psc=1)
- [USB microphone](https://www.amazon.com/gp/product/B014MASID4/ref=oh_aui_detailpage_o06_s00?ie=UTF8&psc=1)
- [Batteries](https://www.amazon.com/gp/product/B00U1U7K02/ref=oh_aui_detailpage_o07_s00?ie=UTF8&psc=1) with [Battery holder](https://www.amazon.com/gp/product/B01505LWDI/ref=oh_aui_detailpage_o07_s00?ie=UTF8&psc=1)
- [5V relay](https://www.amazon.com/gp/product/B00E0NTPP4/ref=oh_aui_search_detailpage?ie=UTF8&psc=1)
- [Chickens](https://cse.google.com/cse?cx=008732268318596706411:nhtd4cwl5xu&q=chickens&oq=chickens&gs_l=partner.3...1329.2438.0.2513.10.9.0.1.1.0.152.791.3j5.8.0.gsnos%2Cn%3D13...0.981j163459j9j1..1ac.1.25.partner..4.6.472.KwyGWJjj03s#gsc.tab=0&gsc.q=chickens%20for%20sale&gsc.sort=). No chickens? No problem, it will just be very boring.

## Setup

### Setup Raspbery Pi

Plug in the USB microphone, install new image of Raspbian, and attach the camera. Setup the camera using `raspi-config` and then setup the following.

#### [Wifi](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md)

Make sure this WiFi will work outside.

`sudo vim /etc/wpa_supplicant/wpa_supplicant.conf`

    network={
      ssid="SOMETHING"
      psk="PASSWORD"
    }


#### Download packages

```
sudo apt-get install apcalc python3 python3-setuptools zsh openssh-server openssh-client tree git vim htop python3-pyaudio python3-pil python3-numpy python3-rpio.gpio
```

#### [Setup audio](http://raspberrypi.stackexchange.com/questions/37177/best-way-to-setup-usb-mic-as-system-default-on-raspbian-jessie)

`sudo nano /usr/share/alsa/alsa.conf` scroll down until you find the lines

    defaults.ctl.card 0
    defaults.pcm.card 0

and change them to

    defaults.ctl.card 1
    defaults.pcm.card 1

## Run chicken monitoring program

```
git clone https://github.com/schollz/hens.git
cd hens
sudo python3 main.py
```

## Run chicken web server

First install [Go1.7+](https://golang.org/dl/).

```
git clone https://github.com/schollz/hens.git
cd hens/server
go build
./server
```
