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

## Usage
To use these scripts, you need to do the following:

 - Make sure that you have Ansible installed on the development laptop you will use alongside your Raspberry Pi.
 - Expand the filesystem on the PI manually (automatic expanding is in the backlog).
 - Create a keypair and copy the public SSH key to the `public_keys` directory.
 - Execute the `./run` script.

## Variables

### SSH

Having successfully setup key-based ssh, you can select to disable password-based login. In `playbook.yml`:

	vars:
	 	- disable_password_login : ( yes | no )

### Wifi

If you want to configure wifi, you'll need your Wifi SSID and your Wifi Pre-shared Key (PSK). When you have them
edit the file `playbook.yml` and enter the details in the relevant vars fields.

	  vars:
    	- wifi_ssid: "<your wifi SSID in here>"
    	- wifi_psk: "<your wifi pre-shared key/password here>"

### Hostname

You can use the `hostname` tag to change the system hostname of your RPI. Change the following variables in `playbook.yml`:

	vars:
		- hostname: <your new hostname in here> 
 
## Defaults
Sensible (for me) defaults are provided for the keyboard layout and timezone. To change them, edit `playbook.yml`, changing:

    vars:
        - keyboard : <your keyboard code>
        - timezone : <your timezone>
        
For a list of timezones, see the `tz` field in [this table](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)