# iodine

The purpose of this is to do DNS tunneling, to bypass some wifi
security.

On the server, run:

    iodined -f -P password 10.7.0.1 tunnel.yourdomain.com

To make it run automatically (assuming you used the debian package) edit
/etc/default/iodined to reflect the following:

    START_IODINED = "true"
    IODINED_ARGS = "10.7.0.1 tunnel.yourdomain.com"
    IODINED_PASSWORD = "password"

On the client run:

    iodine -f tunnel.yourdomain.com

Afterwards use an ssh tunnel to route traffic.
