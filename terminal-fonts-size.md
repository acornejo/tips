# Terminal-Fonts-Size

To fix blurry fonts in gnome-terminal:

    cd /etc/fonts/conf.d
    rm 10-hinting-medium.conf
    ln -s ../conf.avail/10-hinting-full.conf
    rm 10-no-sub-pixel.conf
    ln -s ../conf.avail/10-sub-pixel-rgb.conf

To change the default size of the terminal:

    vim /usr/share/vte/termcap/xterm
    # the line with the following describes an 80x24 term
    :co#80:it#8:li#24:\
