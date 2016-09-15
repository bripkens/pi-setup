# Raspberry PI Base Setup
This repository provides a set of Ansible scripts that you can use to setup your Raspberry PI.

## What it does
 - Upgrades the system.
 - Installs a set of commonly used tools like vim, Git and tmux.
 - Configures NTP to the Europe/London time zone.
 - Switches the keyboard layout to an Enlgish one.
 - Copies your public key to the RPI and disables password based SSH login.

## Usage
To use these scripts, you need to do the following:

 - Make sure that you have Ansible installed.
 - Expand the filesystem on the PI manually (automatic expanding is on the TODO list).
 - Copy your public SSH key to the `public_keys` directory and remove mine.
 - Execute the `./run` script.

## TODO
 - [ ] automatic expanding of the root filesystem + reboot
 - [ ] automatic configuration of the WIFI
 - [ ] configure static IP
 - [ ] IP table configuration
 - [ ] change of default password?
 - [ ] Is there a way to set linux to only accept passwordless ssh for security?