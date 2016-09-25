# Raspberry PI Base Setup
This repository provides a set of Ansible scripts that you can use to setup your Raspberry PI.

## What it does
 - Upgrades the system.
 - Installs a set of commonly used tools like vim, Git, tmux.
 - Configures NTP to your time zone.
 - Switches the keyboard layout to your preference.
 - Copies your SSH public key to the RPI.
 - Optionally disables password based SSH login.
 - Configures wifi connection - DHCP assigned IP.
 - Changes the RPI system `hostname` (writes that to the hosts file in this repo for future plays).

## Pre-requisites

- Install Ansible on the laptop you will be using alongside your Raspberry Pi.
- Expand the Filesystem on the Pi.
- Create a keypair and copy the public SSH key to the `public_keys` directory. See [the setup doc](SETUP.md) for instructions.

### Variables

#### SSH

Having successfully setup key-based ssh, you can select to disable password-based login. In `playbook.yml`:

	vars:
	 	- password_login_permitted : ( "yes" | "no" )

I think these values need to be quoted so that ansible treats them as a string and not boolean.

#### Wifi

If you want to configure wifi, you'll need your Wifi SSID and your Wifi Pre-shared Key (PSK). When you have them
edit the file `playbook.yml` and enter the details in the relevant vars fields.

	  vars:
    	- wifi_ssid: "<your wifi SSID in here>"
    	- wifi_psk: "<your wifi pre-shared key/password here>"

#### Hostname

You can use the `hostname` tag to change the system hostname of your RPI. Change the following variables in `playbook.yml`:

	vars:
		- hostname: <your new hostname in here> 
 
### Defaults
Sensible (for me) defaults are provided for the keyboard layout and timezone. To change them, edit `playbook.yml`, changing:

    vars:
        - keyboard : <your keyboard code>
        - timezone : <your timezone>
        
For a list of timezones, see the `tz` field in [this table](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)

## Usage

Set the variables that are important to you (see below).

Run the `./deploy` script. Some examples:
 
* Run everything
 	
	$> deploy
 		
* Run just the basics play
 	
	$> deploy basics
 		
* Run just the wifi play
 	
	$> deploy wifi
 		
* Run just the hostname play
 	
	$> deploy hostname
 		
 		  

