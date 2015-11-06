# SSH-proxy

To setup a local socks proxy:

    ssh -nNT -D 8080 remoteserver
    chrome --proxy-server="socks5://localhost:8080"

To connect to host HostC, going through HostB, going through HostA:

    ssh -At HostA ssh -At HostB ssh -A HostC

Notice that the -t (create a pseudo-tty) is not required for the last
hop. The -A is used to forward the ssh-agent.
