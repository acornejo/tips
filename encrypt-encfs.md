# encrypt encfs

To mount an encrypted volume:

    encfs ~/.hidden ~/visible

To unmount an encrypted volume:

    fusermount -u ~/visible

Install in Debian:

    apt-get install encfs

Install in OSX:

    brew install Caskroom/cask/osxfuse
    brew install encfs
