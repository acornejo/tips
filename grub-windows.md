# Grub-windows

Add your windows partition in /boot/grub/menu.lst:

    title WinXP
        rootnoverify (hd0,0)
        makeactive
        chainloader +1
