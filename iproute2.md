# iproute2

This will show your links or interfaces; so you know their names and use
them after "dev"

    ip link show

get your current IP addresses

    ip addr show

enable your link

    ip link set dev eth0 up

disable your interface

    ip link set dev eth0 down

set an IP address

    ip addr add 192.168.1.100/24 dev eth0

add another IP address to your interface (2 IP addresses)

    ip addr add 192.168.1.101/24 dev eth0

set a default route (pretend that the default gateway is 192.168.1.254)

    ip route add default via 192.168.1.254

to set a route for a specific interface

    ip route add 192.168.1.0/24 dev eth0

to see the route followed to reach an ip

    ip route get 10.10.24.2
