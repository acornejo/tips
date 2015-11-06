# Share-Internet

The internet connection is on wlan0 and it wants to share this
connection with a computer (or group of computers) connected through
eth0.

At the server the following commands should be executed.

Enable ipv4 forwarding:

    sysctl net.ipv4.ip_forward=1
    execute sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

Setup forwarding rules:

    iptables -A FORWARD -o wlan0 -i eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
    iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
    iptables -A POSTROUTING -t nat -j MASQUERADE

Use forward (at client):

    route add default gw 192.168.1.154
