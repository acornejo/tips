# encrypt loop luks

Create image:

    dd if=/dev/urandom bs=1M count=100 of=file

Create encrypted device node pointing to file:

    losetup /dev/loop0 file
    cryptsetup luksFormat /dev/loop0

Make encrypted container avaialble in /dev/mapper/secret:

    cryptsetup luksOpen /dev/loop0 secret

Create filesystem:

    mkfs.ext2 /dev/mapper/secret
    tune2fs -c 0 -i 0 /dev/mapper/secret

Destroy device node:

    cryptsetup luksClose secret
    losetup -d /dev/loop0

In the future to mount the container again do: losetup /dev/loop0 file
cryptsetup luksOpen /dev/loop0 secret mount /dev/mapper/secret
/media/secret

Unmount the filesystem:

    umount /media/secret
    cryptsetup luksClose secret
    losetup -d /dev/loop0
