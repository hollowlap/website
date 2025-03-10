# Installation

- [Overview](#overview)
- [Applications](#applications)
- [Chrome OS](#chrome-os)
- [Upgrading](#upgrading)
- [Issues](#issues)

## Overview

### Video Overview

[https://www.youtube.com/watch?v=Sh5W7vw9Lqc](https://www.youtube.com/watch?v=Sh5W7vw9Lqc)

> (credit to [Retro Game Corps](https://www.youtube.com/channel/UCoZQiN0o7f36H7PaW4fVhFw) for creating this video)

### Installation Overview

#### Step 0: Charge Your Console!

These consoles can act really strangly at low charge. Please charge your console to 100% before you install AmberELEC.

#### Step 1: Download

Download the latest img.gz image from [https://github.com/AmberELEC/AmberELEC/releases/latest](https://github.com/AmberELEC/AmberELEC/releases/latest).

#### Step 2: Unzip

Unzip the .img.gz file so that you have a .img file. Skipping this step can lead to a corrupted install.

#### Step 3: Flash

* Open your favorite image writer (we will use [balenaEtcher](https://www.balena.io/etcher/) as an example).
* Click on "select image" and select the image you've just downloaded.
* Click on "select drive" and choose your target MicroSD card.
* Click on "flash", make yourself a coffee, wait a bit and you're set!

#### Step 4: Initialize

Put your MicroSD card into slot 1 of your your retro device. If your device has a second SD slot, please leave it empty during initialization. AmberELEC should create your games partition and reboot. It's normal for this process to take a minute or two.  After setting up for the first time, subsequent boots will be faster.

#### (Optional) Step 5: Second SD

If you're using a system that supports a second SD card and you want to use a second SD card for your games, now is the time to set it up. Format the card as ExFAT or ext4. Don't put anything on the card yet. Turn your console off, put the game SD card in the second slot, and turn it back on. During bootup, AmberELEC will create the folder structure for your second SD card. Now you can transfer games to and from your second SD card using your preferred method.

#### Notes
* **RG351V/MP/RG552 Second SD Card**: RG351V/MP users may use a large MicroSD in the first socket, or a smaller MicroSD with a larger card in the second socket. The second card must have a single partition or whole card formatted with exFAT or ext4. FAT filesystems are not supported as it lacks support for filesystem features in use by AmberELEC. NTFS is not currently supported and may be added in a future release. This card should be left out of the console on first initialization.

## Applications

### Unzipping gz files

#### Windows

Windows cannot unzip .gz files natively. The free and open-source software [7-zip](https://www.7-zip.org/) (external link) handles .gz files, as well as most other files. It's strongly recommended that you install it.

#### OSX

OSX can unzip .gz files natively. You should be able to double click on the .gz file to unzip it. Some systems have been known to both unzip and mount in a single step. If this is happening, you can just unzip the .gz file by right clicking (or CTRL+click if you don't have a right mouse button) and choosing `Open With > Archive Utility`. If you're still having trouble with it, you can try [The Unarchiver](https://theunarchiver.com/), a free but not open-source unzipping software.

#### Linux

Most Linux distributions can unzip .gz files natively. If you have any trouble, you can probably find an answer by searching for your distro name + .gz.

### Writing the Image

#### Windows

There ara many image writers that work fine on Windows. [Win32 Disk Imager](https://win32diskimager.org/), [balenaEtcher](https://www.balena.io/etcher/), [Rufus](https://rufus.ie/en/), and [USB Image Tool](https://www.bytesin.com/software/Download-USB-Image-Tool/)  are all known to be able to flash the image successfully.

#### OSX

There's not a lot of experience from people flashing on Mac, but you may have success with the [rpi-imager](https://github.com/raspberrypi/rpi-imager).

#### Linux

Users have reported issues using the standard tools (mkfs, Gnome Disk Utility), so the preferred SD writing tool on Linux is the [rpi-imager](https://github.com/raspberrypi/rpi-imager).

## Chrome OS

While Chrome OS is a Linux distribution, the usual image writers don't work on it. Chrome OS has normal SD functions disabled on purpose for security reasons. The solution is to use the Chromebook Recovery Utility application. This application was made specifically to flash a Chrome OS image to an SD card, but it can be used to flash any image in a recognized format.

### Installation Steps

* Download the latest img.gz image from [https://github.com/AmberELEC/AmberELEC/releases/latest](https://github.com/AmberELEC/AmberELEC/releases/latest). Make sure you get the right image for your device.
* Unzip the .img.gz image. You should have a file called something like `351ELEC-RG351P.aarch64-YYYYMMDD.img`
* Append .bin to the end of the .img file. The filename should now be similar to `351ELEC-RG351P.aarch64-YYYYMMDD.img.bin`
* Run the Chromebook Recovery Utility application. Click the settings button in the upper right, and select "Use Local Image"
* Select your Micro SD card as the target, and continue through the process. The card will be flashed, and you'll be ready to put it into your console to initialize.

## Upgrading

To upgrade from a previous release:

* Download the latest `.tar` package from [the project's GitHub repo](https://github.com/AmberELEC/AmberELEC/releases/latest).  Make sure you get the right image for your device.
* Move the `.tar` package file to the `update` directory on your GAMES partition (this can be done any way you like, easiest would be to just insert your microSD card back into your computer and copy it with your file manager).
* Reboot your device.  AmberELEC will notice the presence of the file, check it for completeness and apply the update.

## Issues

### General

#### Bad SD cards

It's strongly recommended that you use a relatively new MicroSD card made by a well respected brand (Samsung, Sandisk, etc). Many unbranded MicroSD cards are extremely prone to failure at any moment. In addition, watch out for counterfeit cards. There are unscrupulous people selling counterfeit cards that claim to be made by a name brand, but aren't. Many of these cards also misrepresent how much space they have on them, both on their packaging and to your OS.

Finally, some very old SD cards can be too slow for reliable use. This is especially common with 4GB SD cards, as many companies no longer bother with making new 4GB SD cards.

#### Fixing Bad Blocks

Some SD cards develop (or are shipped with) bad blocks, and this can cause any of the issues listed below. The [Official SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/) can fix some of them, and should be an early step in fixing and diagnosing issues. This won't fix all bad blocks, and it cannot fix other issues with knockoff, clone, or bad unbranded SD cards.

### Flashing

#### I'm using a MicroSD -> SD adapter, and the flash won't write to the SD card

MicroSD to SD adapters have a physical read-only switch on them. Try changing this switch to the other position and flashing the card again.

#### I'm getting a write error when flashing

This can sometimes be fixed by using the official [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter/) application. If that doesn't work you may have a bad SD card.

### Initialization

#### System failure error message

This can be caused when the compressed image is written to the SD card rather than the uncompressed image. If you flashed using the .img.gz rather than unzipping it and flashing with the .img file, please try unzipping the .img.gz file and flashing again.

This can also just happen randomly when booting from the SD card for the first time. Try booting from it again and see if it works.

#### Initialization never finishes/takes forever

Unfortunately, there are a number of things that can cause this. The first thing to check is whether you're using the correct image for your device. This problem can be caused if you're using the P/M image on a V device or the V image on a P or M device.

This can also be caused by a corrupted flash, which can happen for any number of reasons. A bad SD card (always use a good quality name brand card if possible), a bad SD adapter, an issue with the particular SD or USB port, or even just a problem with your computer.

The simplest things to try are switching USB or SD ports and using a different SD flashing application. If that doesn't work, you might try using a different SD card, or a different computer. You can also try flashing a different OS (such as ArkOS or Lakka) and seeing if they have any issues. If those OSes don't work either, you have some sort of hardware problem, either with your console, SD card, port, or computer. If they do work, there's some sort of software issue going on. Knowing that can help if you ask for assistance with it in our [Discord](https://discord.com/invite/R9Er7hkRMe).
