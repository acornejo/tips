# Core-Dumps

To enable once:

    sysctl kernel.core_pattern="/tmp/core.%e.%p.%h.%t"
    sysctl fs.suid_dumpable=1
    ulimit -c unlimited

To persist across reboots:

    echo " * soft core unlimited" >> /etc/security/limits.conf
    echo "kernel.core_pattern=/tmp/core.%e.%p.%h.%t" >> /etc/sysctl.conf
    echo "fs.suid_dumpable=1 >> /etc/sysctl.conf
