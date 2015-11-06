# Mounting dd image of drive

NOTE: This works for an entire drive, not a aprtition

1.  Use fdisk to determine the offset to the partition:

     fdisk -u drive.img
     # Command (m for help): p
     # Disk drive.img: 1024 MB, 1024966656 bytes
     # 32 heads, 62 sectors/track, 1009 cylinders, total 2001888 sectors
     # Units = sectors of 1 * 512 = 512 bytes

     #   Device Boot      Start         End      Blocks   Id  System
     #drive.img   *          62     2001855     1000897   83  Linux

Since the sectors are of size 512, and it starts at 62, the offset is
512\*62=31744

2.  Mount to examine the image:

    mount -r -o loop,offset=31744 drive.img /media/drive
