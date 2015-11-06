# CD DVD burning

Create an ISO from CD/DVD

    dd if=/dev/cdrom of=image.iso bs=1024

Create a BIN/CUE from CD/DVD

    cdrdao read-cd --read-raw --datafile image.bin --device 0,0,0 --driver generic-mmc-raw image.cue

Create an ISO from a folder (Use -RJ instead of -J to preserve
permissions+links)

    mkisofs -J -V 'title' -o image.iso /folder/

Mount an ISO (assumes loop module is loaded)

    mount image.iso /media/iso/ -t iso9660 -o loop

Burning ISO's

To get device first do

    cdrecord -scanbus

Assuming device = 1,1,0
    cdrecord -v dev=1,1,0 speed=48 [-multi] image.iso

Burning a cue/bin

    cdrdao write --device 0,0,0 --speed 48 somefile.cue

Burning DVD image

    growisofs -speed=8 -dvd-compat -Z /dev/dvdrw=image.iso

Duplicating a CD

    cdrdao copy --source-device /dev/cdrom --device /dev/cdrw --on-the-fly

Multisession burning

1. create the first ISO
2. burn and add the -multi flag
3. cdrecord -msinfo /dev/cdrw to get offset, assume 0,12639
4. create the second ISO, append -C 0,12639 to the command line
5. burn and add the -multi flag
6. goto step 3
