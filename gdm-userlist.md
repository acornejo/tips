# GDM-userlist

Since Ubuntu Karmic (perhaps earlier) GDM displays a list of users in
the login screen. This is inconvenient for several reasons, especially
to those which use systems with more than a few users. To disable user
list in GDM:

    sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
