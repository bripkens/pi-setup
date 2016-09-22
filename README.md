# Raspberry PI Base Setup
This repository provides a set of Ansible scripts that you can use to setup your Raspberry PI.

## What it does
 - Upgrades the system.
 - Installs a set of commonly used tools like vim, Git, tmux and mlocate (`updatedb` & `locate ...`).
 - Configures NTP to your time zone.
 - Switches the keyboard layout to your preference.
 - Copies your public key to the RPI
 - Can be used to disable password based SSH login.

## Usage
To use these scripts, you need to do the following:

 - Make sure that you have Ansible installed on the development laptop you will use alongside your Raspberry Pi.
 - Expand the filesystem on the PI manually (automatic expanding is in the backlog).
 - Create a keypair and copy the public SSH key to the `public_keys` directory.
 - Execute the `./run` script.
 
## Defaults
Sensible (for me) defaults are provided for the keyboard layout and timezone. To change them, edit `playbook.yml`, changing:

  vars:
    - keyboard : <your keyboard code>
    - timezone : <your timezone> (from the `tz` field in [this table](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
