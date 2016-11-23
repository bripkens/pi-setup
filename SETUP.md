## Before You Get Started

### You'll need:

* A Raspberry Pi (I've only tested this on a B+), but it seems like it should work on others.
* A wifi dongle. Mine is an Edimax.
* Power (see below)
* An ethernet cable. Mine is "Go-faster Blue", but I heard a rumour colour doesn't effect BW. I remain skeptical.
* A microSD card. I'm just using one a 16GB card from maplins.
* A microSD card reader of some sort. My Mac doesn't have a port for microSD so I use an 'Integral MicroSD' reader, which is a USB reader that has a little slot for microSDs.
* Access to a wifi router. You'll need to be able to connect your Pi to it via Ethernet and be able to power your Pi at the same time.

A note about power: when I first started out, I used an old nokia charger (UK wall plug --> micro USB) but it didn't work because it wasn't providing enough current to the Pi. I now successfully use an apple iPhone charger plug (which has a female USB) and a USB --> microUSB cable. Whatever you decide to use, check the spec of the plug part; it usually states it's output volts and amps in font size 2.5 somewhere. If you're shy on plug sockets, get a 10,000 MAh battery; you won't regret it.

### You won't need:

* Keyboard
* Mouse
* HDMI cable
* A monitor

*(Unless things go tits-up, in which case you might)*

This is all about automating the installation and configuration of your Pi. It's for people who might not want to remember all those magical incantations and learn-by-doing installations this time round. I'm imaging you searched for 'Get me to the point with a Pi where I can develop and install my App (goddamit)' and ended up here.

## Installing the Operating System

### 1. Download the latest Raspbian Image. I'm using Jesse.

You can download from [the official raspbian download page](https://www.raspberrypi.org/downloads/raspbian/). It's about 4GB so it might take a while.

### 2. Download and Install PiBaker
PiBaker is an easy Mac Utility for writing images to SD cards. [AlternativesTo.com](http://alternativeto.net/software/applepi-baker/about/) lists the Win32 Disk Imager, which might work for you on Windows. Download PiBaker from [here](http://www.tweaking4all.com/software/macosx-software/macosx-apple-pi-baker/). Scroll down to the green boxes to find the actual download button.

### Write image to MicroSD

![Image of the PiBaker UI](/images/piBakerWrite.png)

1. Insert your USB/SD card
2. Open PiBaker; you will probably have to provide your sudo password.
3. Check that there is something in the box labeled 'C' in the image above.
4. Use the file browser (labeled 'A' in the image above) to find your downloaded raspbian .img file.
5. Click 'Restore Backup' (labeled 'B').
6. If it all goes well, you won't see any errors and it'll provide a message saying you've successfully written your image and that it's automatically unmounted and ejected the disk. Good.

### Load and boot.

1. Stick the microUSB into your Raspberry Pi.
2. Connect the Pi to the router using the Ethernet cable.
3. Connect your Wireless dongle to the Pi.
4. Connect your Pi to the power.

## Passwordless SSH and Creating Keys

We're going to create a key pair that allows you to ssh into your raspberry pi from your laptop without having to
use the password every time. It

To create a new keypair, follow the following instructions. This assumes you're on a \*nix flavoured laptop/box.

1. Download or clone this repo.

2. Generate a key:

		$> ssh-keygen
		Generating public/private rsa key pair.
		Enter file in which to save the key (/Users/robrant/.ssh/id_rsa): /Users/robrant/.ssh/pikey.pem
		Enter passphrase (empty for no passphrase): 
		Enter same passphrase again: 
		Your identification has been saved in /Users/robrant/.ssh/pikey.pem.
		Your public key has been saved in /Users/robrant/.ssh/pikey.pem.pub.
		The key fingerprint is:
		SHA256:<my sha was in here>
		The key's randomart image is:
 	
3. Change the name of the public key to `pikey.pub` and copy into the `pi-setup/public_keys` directory inside the downloaded/cloned version of this repository.
