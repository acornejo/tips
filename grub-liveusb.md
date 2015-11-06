# Grub LiveUSB

It is now possible to install the grub bootloader in your USB drive.

The following instructions will wipe your device, and create a new fat32
partition:

    FOLDER="/media/usb"
    DEVICE="/dev/usbdevice"

    # clean boot sector
    dd if=/dev/zero of=$DEVICE bs=512 count=1
    # create label
    parted $DEVICE mklabel msdos
    # create partition table
    parted $DEVICE mkpartfs p fat32 0 100%
    # set boot flag
    parted $DEVICE set 1 boot on
    # install grub

Now installing grub is easy:

    mount ${DEVICE}1 $FOLDER
    grub-install --no-floppy --root-directory=$FOLDER $DEVICE

To configure grub to boot an ISO file in your usb stick:

    cat << EOF > $FOLDER/boot/grub/grub.cfg
    menuentry "LiveCD"
    {
        loopback loop /boot/iso/ubuntu.iso
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu.iso noeject noprompt --
        initrd (loop)/casper/initrd.lz
    }
    EOF
