
## Usage
To use this Ansible playbook, first set some variables and then run the `./run`
script from the command line. Examples provided below.

## Variables

### SSH

Having successfully setup key-based ssh, you can select to disable password-based login. In `playbook.yml`:

	vars:
	 	- password_login_permitted : ( "yes" | "no" )

I think these values need to be quoted so that ansible treats them as a string
and not boolean. **It is currently recommended that you set this to "yes" - it needs
some more testing and [then a fix](https://github.com/robrant/pi-setup/issues/6).**

### Wifi

It's assumed that the Pi is currently connected via Ethernet to your router.
If you want this playbook to configure wifi, you'll need your Wifi SSID and
your Wifi Pre-shared Key (PSK). Edit the file `playbook.yml` and enter the
details in the relevant vars fields.

	  vars:
    	- wifi_ssid: "<your wifi SSID in here>"
    	- wifi_psk: "<your wifi pre-shared key/password here>"

### Hostname

You can use the `hostname` tag to change the system hostname of your RPI.
Change the following variables in `playbook.yml`:

	vars:
		- hostname: <your new hostname in here>

## Defaults
Sensible (for me) defaults are provided for the keyboard layout and timezone.
To change them, edit `playbook.yml`, changing:

    vars:
        - keyboard : <your keyboard code>
        - timezone : <your timezone>

For a list of timezones, see the `tz` field in [this table](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
