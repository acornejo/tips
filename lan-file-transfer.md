# LAN-File-Transfer

On the receiving end (omit -p in BSD):

    PORT=${RANDOM}
    echo "listening on port ${PORT}"
    nc -l -p ${PORT} | tar xzvf -

On the sending end:

    tar czvf -  /Some/Folder | nc {HOST} ${PORT}
