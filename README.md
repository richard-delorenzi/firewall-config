firewall-config
===============

A very strict firewall config, to use with http and dns proxys.

Requires Linux kernel and ufw.
run `./setup-firewall`

Most of the config is in `setup-firewall` and uses ufw, but some uses iptables directly and is in `my-filewall` this script is copied to `/etc/init.d` by the setup script.
