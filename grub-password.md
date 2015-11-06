# Grub-password

Generate password:

    yes password | grub-md5-crypt 2>/dev/null | tail -n1

Add password to grub:

    # Add to thge top of /boot/grub/menu.lst
    password --md5 ${md5password}

To hide the menu: hiddenmenu
