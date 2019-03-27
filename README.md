# munin-areca-plugin
Munin plugin for monitoring various Areca RAID cards via the official cli64 utility

## Prerequisites
arcmsr modules must be loaded in the kernel

Install Areca cli64 utility (https://www.areca.com.tw/support/downloads.html) and add it to your $PATH

Verify cli64 works with the command `cli64 hw info`

## Installation
Place in /usr/share/munin/plugins, then create symlinks named `areca_temp` and `areca_volt` to it from /etc/munin/plugins.

Edit /etc/munin/plugin-conf.d/munin-node and add:
```
[areca*]
user root
```

Optionally, if you want to exclude unused ports from showing up in the graph add
```
env.ignore_tempxx y
```
Where `xx` is the number of the port you want to exclude.

Reload munin config with `sudo service munin-node restart`

## Test Run
Verify the plugin is working by running `sudo munin-run areca_temp` and `sudo munin-run areca_volt`
