# Recover-HD

Go into server and dump your drive:

    ssh deadserver dd if=/dev/hda1 conv=noerror,sync > hda1.img

Mount your drive image and try to recover:

    losetup /dev/loop0 hda1.img
    reiserfsck --rebuilt-tree -S -l recover.log /dev/loop0

Other options are --rebuild-sb and --check, also try:

    mount /dev/loop0 /mnt/recovered
    look in /mnt/recovered or /mnt/recovered/lost+found
    umount /mnt/recovered
    losetup -d /dev/loop0
