# SSH-Tunnel

Consider two machines A and B, where A can ssh to machine B.

Setting 1: Machine A and wants to access www.nytimes.com which is
unreachable/blocked from A, but is reachable from B.

To access www.nytimes.com from A (using a tunnel that goes through B)
you can execute the following in A:

    ssh -nNT -L 1100:www.nytimes.com:80 B

Now A can access www.nytimes.com:80 by accessing instead localhost:1100.

Setting 2: Machine B wants to access mail.local.net which is
unreachable/blocked from B, but is reachable from A.

To access mail.local.net from B (using a tunnel that goes through A) you
can execute the following in A:

    ssh -nNT -R 1100:mail.local.net:80 B

Now B can access mail.local.net:80 by accessing instead localhost:1100.
