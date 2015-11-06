# sudo

To enable password-less sudo access to current user:

    echo "${USER} ALL=(ALL)NOPASSWD: ALL" | sudo tee /etc/sudoers.d/${USER}-sudo
