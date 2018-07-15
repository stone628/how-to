# objective
- build mobile linux dev box, with WIFI and bluetooth support

# hardware
- Raspberry Pi 3 or above
- Raspberry Pi compatible LCD screen
	- Waveshare 3.5inch LCD + Touch screen

# instructions
- prepare sd-card
	- download raspbian-lite(jessie) image from raspberrypi.org
	- follow install guide at [Installing Operating System Images](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)
> my Wi-fi was not working with raspbian-lite(stretch), so I selected jessie instead.

- initial setup
	- with raspi-config
		- user password
		- localization options
			- locale: en-US.UTF-8, ko_KR.UTF-8(or your own locale)
			- timezone: your own timezone
			- keyboard layout: your own keyboard layout
			- Wi-fi country: your country
		- interfacing options: SSH server, SPI (for lcd screen)
		- expand filesystem
  - minimal GUI
    - follow instruction guide at [Raspbian Lite Guide - GUI](https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=133691&sid=07c6d0e28b623d7b521ca6b4bc3be8ac)
    - stripped Xorg Display Server + stripped RPD(Raspberry Pi Desktop) + LightDM LoginManager
      - ```sudo apt-get install --no-install-recommends xserver-xorg```
      - ```sudo apt-get install --no-install-recommends xinit```
      - ```sudo apt-get install --no-install-recommends raspberrypi-ui-mods lxsession pi-greeter rpd-icons gtk2-engines-clearlookspix```
      - ```sudo apt-get install lightdm```
  - touch screen
    - follow instructions at [WaveShrare 3.5inch RPi LCD(A)](https://www.waveshare.com/wiki/3.5inch_RPi_LCD_(A))
  - minimal apps
    - terminal(lxterminal), touch-screen calibrator(xinput-calibrator)
    
