# network-config

To setup an interface to be managed through dhcp, edit
/etc/network/interfaces and add the following:

    auto $iface
    allow-hotplug $iface
    iface $iface inet dhcp

The hotplug is only required for interfaces that can be physically
removed or turned-off (usually for laptops).

To setup an interface to be managed statically, edit
/etc/network/interfaces and add the following:

    auto $iface
    iface $iface inet static
            address 10.10.100.100
            gateway 10.10.1.1
            netmask 255.255.0.0
            dns-search example.com example.net
            dns-nameservers 10.10.1.2 10.10.1.2

See https://wiki.debian.org/NetworkConfiguration for more info.
