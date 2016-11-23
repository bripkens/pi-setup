# Before You Get Started

'''You'll need''':
* A Raspberry Pi (I've only tested this on a B+), but it seems like it should work on others.
* A wifi dongle. Mine is an Edimax.
* Power (see below)
* An ethernet cable. Mine is "Go-faster Blue", but I heard a rumour colour doesn't effect BW. I remain skeptical.
* A microSD card. I'm just using one a 16GB card from maplins.
* A microSD card reader of some sort. My Mac doesn't have a port for microSD so I use an 'Integral MicroSD' reader, which is a USB reader that has a little slot for microSDs.

A note about power: when I first started out, I used an old nokia charger (UK wall plug --> micro USB) but it didn't work because it wasn't providing enough current to the Pi. I now successfully use an apple iPhone charger plug (which has a female USB) and a USB --> microUSB cable. Whatever you decide to use, check the spec of the plug part; it usually states it's output volts and amps in font size 2.5 somewhere.

'''You won't need:''' Keyboard, mouse, HDMI cable or a monitor. Unless things go tits-up, in which case you might.

# Installing the Operating System

Instructions for setting up your pi before using the ansible playbook.

Download PiBaker

## Expand the file system



## Passwordless SSH and Creating Keys

We're going to create a key pair that allows you to ssh into your raspberry pi without having to
use the password every time. 

Create a new keypair:
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
 	
Change the name of the public key to `pikey.pub` and copy into the `pi-setup/public_keys` directory.
