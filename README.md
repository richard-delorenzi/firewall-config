firewall-config
===============

A very strict firewall config, to use with http and dns proxys.

It blocks almost everything, with some exceptions of ssh, and a few specific sites, it also allows the users proxy and dnsmasq through. These “users” run the squid web proxy and dns proxy, they fetch stuff on our behalf, if squid-guard is properly installed then squid will filter what we can recieve. The dns config below, and the filewall ensure we only connect to trusted dns servers.

Requires Debian with Linux kernel (could easily be modified to work with any Gnu/Linux system, ufw, a proxy on port 3128, and dnsmasq

    apt-get install dnsmasq
    apt-get install squid3
    apt-get install ufw

now configure dnsmasq

    cat <<- end >/etc/dnsmasq-resolv.conf
    nameserver 8.8.8.8
    nameserver 8.8.4.4
    #nameserver [2001:4860:4860::8888]
    #nameserver [2001:4860:4860::8844]
    end

now configure squid: I can't remember the details, it may just work without changing any thing.

    ./setup-firewall

Most of the config is in `setup-firewall` and uses ufw, but some uses iptables directly and is in `my-filewall` this script is copied to `/etc/init.d` by the setup script.
