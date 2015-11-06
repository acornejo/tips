# Gitosis-Mirroring

How to mirror the foo.git gitosis repository in github.com? (same thing
works for bitbucket.org, gitorious.org, etc)

1.  Create a passwordless ssh-key for your gitosis user:

    sudo -u gitosis -H ssh-keygen -t rsa

2.  Add the new ssh key to your github account.
3.  Create an empty foo repository in github.
4.  Setup the mirror from gitosis -> github:

    sudo -u gitosis -H -s cd \~/repositories/foo.git
    git remote add github git@github.com:$user/$(basename `pwd`)
    echo -e '\#!/bin/sh\nexec git push --mirror github >> \~/github.log 2>&1' > hooks/post-update
    chmod 755 hooks/post-update
    hooks/post-update
