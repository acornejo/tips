# WPA

Configure wpa\_supplicant:

    cat << EOF > /etc/wpa_supplicant.conf
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev

    network = {
    ssid="ssidwithwpa"
    psk="password"
    key_mgmt=WPA-PSK
    }

    network = {
    ssid="ssidwithwep"
    key_mgmt=NONE
    wep_key0=HEXKEY
    }

    network={
    ssid="openssid"
    key_mgmt=NONE
    id_str="static_ssid"
    }

    network={
    key_mgmt=NONE
    }
    EOF

Edit /etc/network/interfaces and remove anything related to the wireless
interface and add the following:

    cat << EOF >> /etc/network/interfaces
    allow-hotplug wlan0
    iface wlan0 inet manual
        wpa-roam /etc/wpa_supplicant.conf
        wpa-driver wext

    iface default inet dhcp

    iface static_ssid inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
    EOF
