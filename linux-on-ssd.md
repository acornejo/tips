# linux on ssd

# Requirements
 - kernel 3.2 or newer (3.9+ preferred for caching)
 - latest firmware on ssd
 - check no issues on smartctl: `smartctl -a /dev/sda`
 - use ext4 file system

# How to partition
- use ext4 file system
- align parittions to 4kb
- following partitions in order:
  - boot (350mb)
  - root (20gb)
  - swap (1x ram)
  - home (rest)

# Mount options
 - noatime (disable access time writes)
 - discard (automatic trim)
    - DO NOT enable discard in fstab
    - issue_discards = 1 in lvm.conf
    - discard in /etc/crypttab if encrypted
    - run fstrim periodically (weekly)
 - run update-initramfs -u after changing trim flags
 - ramdisk for tmp, run and lock

# Set a low swappiness

edit /etc/sysctl.conf

   vm.swappiness=1

# Set low latency io-scheduler

install sysfsutils


  echo block/sdX/queue/scheduler = deadline >> /etc/sysfs.conf

  OR

  echo deadline > /sys/block/sdX/queue/scheduler
