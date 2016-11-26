
## Usage
To use this Ansible playbook, first set some variables and then run the `./run`
script from the command line. Examples provided below.

## Hosts file

If this is the first time you've run this your default Raspbian OS has a hostname
of `raspberrypi`, which is the hostname provided in the `hosts` file. Only change
this if you either know the IP or have change the hostname on the raspberry pi.

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

## Running

Run the playbook

  $> ./run

Run a specific tag in the playbook (finer grained control of what gets run)

  $> ./run ( basics | wifi | hostname )

You will be prompted for a password twice - once for the login of the `pi` user
which we specify in the `./deploy` script and once for that user to sudo. The
default password for the `pi` user is `raspbian`.
