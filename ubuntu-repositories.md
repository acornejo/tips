# ubuntu-repositories

To install the usual ubuntu repositories (media labe mirror):

    DIST="oneiric"
    cat << EOF > /etc/apt/sources.list
    deb http://ubuntu.media.mit.edu/ubuntu/ ${DIST} main restricted universe multiverse
    deb http://ubuntu.media.mit.edu/ubuntu/ ${DIST}-updates main restricted universe multiverse
    deb http://ubuntu.media.mit.edu/ubuntu/ ${DIST}-security main restricted universe multiverse
    # deb http://archive.ubuntu.com/ubuntu/ ${DIST}-proposed restricted main multiverse universe
    # deb http://debian.csail.mit.edu/debian unstable main contrib non-free
    deb http://packages.medibuntu.org/ ${DIST} free non-free
    deb http://archive.canonical.com/ubuntu ${DIST} partner
    EOF

To setup priorities on repositories:

    DIST="oneiric"
    cat << EOF > /etc/apt/preferences
    Package: *
    Pin: release a=${DIST}-security
    Pin-Priority: 990

    Package: *
    Pin: release a=${DIST}-updates
    Pin-Priority: 900

    Package: *
    Pin: release a=${DIST}-proposed
    Pin-Priority: 400

    Package: *
    Pin: release a=unstable
    Pin-Priority: -1
    EOF
