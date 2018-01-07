# ch340g-ch34g-ch34x-mac-os-x-driver
Latest **macOS Sierra**-compatible driver for devices using the CH340G, CH34G or CH34X chipset. This chipset is used in several Arduino-compatible clones, NejeEngraver and serial-to-USB cables.

## Introduction

Version 1.3 (2016-09-27) of the [OEM driver](http://www.wch.cn/download/CH341SER_MAC_ZIP.html) for the CH34x chipset currently causes a kernel panic (a.k.a. *crash*) when installed on **macOS Sierra**. To resolve this issue, please download and install the driver in this repo.

Version 1.4 (2017-01-11) of the [OEM driver] driver was released and now signed and works for OS X 10.9 and above.  
Download from: http://www.wch.cn/download/CH341SER_MAC_ZIP.html

Neje Laser Engraver DK-8-PRO is an awesome small laser engraver from China.  OS X Application for this engraver is available at: https://github.com/AndyQ/NejeLaserEngraver

## Installation

* Remove the old driver by issuing one of the following commands (depending on your installation):
  * `sudo rm -rf /System/Library/Extensions/usb.kext`
  * `sudo rm -rf /Library/Extensions/usbserial.kext`
*  Restart your Mac.
*  Double-click on the `CH34x_Install_V1.3.pkg` file.
*  Restart your Mac.
*  Plug in your device. It should now be listed under the `/dev` directory. Examples:
  * `/dev/cu.wchusbserial1410`
  * `/dev/cu.wchusbserial1420`

  V1.4 in macOS 10.12.6 shows with Neje Laser Engraver plugged in to USB Port :
  
     $ ls /dev/tty.w*
     '/dev/tty.wchusbserial1410'


## Installation with Homebrew-Cask

* Install the driver by the following commands:
  * `brew tap mengbo/ch340g-ch34g-ch34x-mac-os-x-driver https://github.com/mengbo/ch340g-ch34g-ch34x-mac-os-x-driver`
  * `brew cask install wch-ch34x-usb-serial-driver`


## Troubleshooting

### Checking if the device is plugged in and USB port is working on it:

* Select About this Mac
* Select "System Report..."
* Select USB and then select USB2.0-Serial.

#### You should see something like the follow, but Product and Vendor ID will vary depending on device:

  USB2.0-Serial:
  
     Product ID:	0x7523
     Vendor ID:	0x1a86
     Version:	2.62
     Speed:	Up to 12 Mb/sec
     Location ID:	0x14100000 / 9
     Current Available (mA):	500
     Current Required (mA):	98
     Extra Operating Current (mA):	0
  
### Confirm ”Mac App Store and identified developers”

Please enter “System Preferences”->”Security & Privacy”->”General” page, below the title ”Allow apps downloaded from:” you should choose the choice 2->”Mac App Store and identified developers” so that V1.4 driver will work normally.

### disable *System Integrity Protection*:

If, and only if, the device is not recognized after the installation (or you cannot install the driver), please disable *System Integrity Protection*:

*  Reboot your Mac into *Recovery Mode* by restarting your computer and holding down `Command+R` until the Apple logo appears on screen.
*  Open the Terminal (Applications > Utilities > Terminal).
*  In the Terminal window, type in `csrutil enable --without kext` (or to fully disable: `csrutil disable`) and press `Enter`.
*  Restart your Mac.

Please share this page!

Regards,  
Adrian Mihalko  
www.mihalko.eu

p.s:
I **LOVE** coffee! Buy me a coffee at:   
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=adriankoooo%40gmail%2ecom&lc=SK&item_name=Adrian%20Mihalko&currency_code=EUR&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted)
