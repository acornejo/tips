# Schroot

install sbuild:

    apt-get install sbuild schroot debootstrap

setup sbuild:

    sbuild-update --keygen
    sbuild-adduser $LOGNAME
    mkdir -p /var/lib/schroot/chroots

create schroot:

    # choose a chroot name
    CHROOT_NAME=precise-amd64
    # target directory to store chroot
    CHROOT_TARGET=/var/lib/schroot/chroots/$CHROOT_NAME
    # debian distribution, complete list in /usr/share/deboot-strap/scripts
    CHROOT_DISTRIBUTION=precise
    # sources.list mirror to use in chroot
    CHROOT_MIRROR=http://archive.ubuntu.com/ubuntu
    # components to use (i.e. main, contrib, non-free..)
    CHROOT_COMPONENTS=main,restricted,universe,multiverse
    # list of additional packages to install
    CHROOT_PACKAGES=apt-utils,pkg-create-dbgsym,pkgbinarymangler,sbuild

    sbuild-createchroot $CHROOT_DISTRIBUTION $CHROOT_TARGET $CHROOT_MIRROR --components=$CHROOT_COMPONENTS --include=$CHROOT_PACKAGES

fix bug https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565613

    sed -i '/exim/d' $CHROOT_TARGET/var/lib/dpkg/statoverride

modify your source schroot:

    schroot -c source:$CHROOT_NAME -u root
    do stuff
    exit
