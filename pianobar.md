# pianobar

To configure it create a file in \~/.config/pianobar/config

To prevent pianobar from asking for a password, you can use a keyring
utility (pip install keyring; keyring set pandora \${YOUREMAIL})

This is the contents of a simple config file:

    user = ${YOUREMAIL}
    password_command = keyring get pandora ${YOUREMAIL}
    autostart_station = 731900974616170908

    format_nowplaying_song =  [36m%a[0m  - [32m%t[0m ([31m%l[0m)
    format_nowplaying_station = [35m%n[0m (id: %i)
    format_list_song = %i) %a - %t%r
