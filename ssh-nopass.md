# SSH-nopass

Generate and copy key to remote host:

    ssh-keygen -t rsa (enter, enter)
    ssh-copy-id remotehost

To create a public/private key pair for someone else do:

    ssh-keygen -t rsa -C john@doe.net -f john_key

You may have to use the IdentityFile option in .ssh/config to
authenticate with a particular key.

To convert to putty format install putty-tools and do:

    puttygen privatekeyfile -O private -o privatekeyfile.ppk
