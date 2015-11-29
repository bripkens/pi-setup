# Raspberry PI Base Setup
This repository provides a set of Ansible scripts that you can use to setup your Raspberry PI.

## What it can for you
 - Upgrades the system.
 - Installs a set of commonly used tools like vim, Git and tmux.
 - Installs Node.js v4.2.2.
 - Configures NTP to the Europe/Berlin time zone.
 - Switches the keyboard layout to a German one.
 - Installs wiringPi and rcswitch-pi.
 - Copies your public key to the RPI and disables password based SSH login.

## Usage
To use these scripts, you need to do the following:

 - Make sure that you have Ansible installed.
 - Expand the filesystem on the PI manually (automatic expanding is on the TODO list).
 - Copy your public SSH key to the `public_keys` directory and remove mine.
 - Execute the `./run` script.

## TODO
 - [ ] automatic expanding of the root filesystem
 - [ ] automatic configuration of the WIFI
