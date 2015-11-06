# encrypt loop aes

Create image:

    dd if=/dev/urandom bs=1M count=100 of=file

Create device node with encryption:

    losetup -e aes256 /dev/loop0 file

Create filesystem:

    mkfs.ext2 /dev/loop0
    tune2fs -c 0 -i 0 /dev/loop0

Destroy device node:

    losetup -d /dev/loop0

To mount the encrypted filesystem:

    mount -o loop,encryption=aes256 -t ext2 file /media/secret

To unmount:

    umount /media/secret
