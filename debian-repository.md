# Debian-Repository

To clean up your repository (remove old packages):

    apt-get autoclean

To create your own apt repository:

    dpkg-scanpackages /var/cache/apt/archives/ /dev/null 2> /dev/null | gzip > /var/cache/apt/archives/Packages.gz

Adding the apt a custom apt repository:

    echo deb ssh:remote: /var/cache/apt/archives/ >> /etc/apt/sources.list
