# Debian-Replicating

On existing system do:

    dpkg --get-selections > /shared/selections

On new system do:

    dpkg --set-selections < /shared/selections
    apt-get dselect-upgrade

As an alternative for a cleaner more manual upgrade (on existing
system):

    dpkg -l | awk '/^ii/{ print $2 }' | grep -v -e ^lib -e -dev -e $(uname -r) > installed.txt

On the new system

    apt-get install $(cat installed.txt | tr '\n' ' ')
