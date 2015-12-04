# gpg agent

Add ssh support, and set key expiration to 5 hrs

    cat << EOF >> ~/.gnupg/gpg-agent.conf
    enable-ssh-support
    default-cache-ttl 18000
    default-cache-ttl-ssh 18000
    write-env-file $HOME/.gnupg/gpg-agent-info
    EOF

Disable ssh-agent in your xsession:

    sed -i '/use-ssh-agent/d' /etc/X11/Xsession.options

To have your Xsession's gpg-agent talk to your console gpg-agent

    ln -sf ~/.gnupg/gpg-agent-info ~/.gnupg/gpg-agent-info-$(hostname)

Remove gnome-keyring from pam

    apt-get purge libpam-gnome-keyring

Tell gnome-keyring not to replace ssh or gpg agents

    mkdir ~/.config/autostart
    cp /etc/xdg/autostart/gnome-keyring-gpg.desktop ~/.config/autostart/
    cp /etc/xdg/autostart/gnome-keyring-ssh.desktop ~/.config/autostart/
    echo "Hidden=true" >> ~/.config/autostart/gnome-keyring-gpg.desktop
    echo "Hidden=true" >> ~/.config/autostart/gnome-keyring-ssh.desktop

Preserve ssh authentication socket while inside sudo

    echo Defaults       env_keep += "SSH_AUTH_SOCK" > /etc/sudoers.d/ssh-auth-sock
