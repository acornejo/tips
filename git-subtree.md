# git-subtree

To subtree-merge an existing repository to the cork/ directory

    git remote add -f cork git://github.com/${USER}/cork.git
    git merge -s ours [--squash] --no-commit cork/master
    git read-tree --prefix cork/ -u cork/master
    git commit -m "Merged changes from cork"

To update the cork/ directory with the latest changes

    git pull -s subtree [--squash] cork master

Using git-subtree things are simpler:

    git remote add -f cork git://github.com/${USER}/cork.git

    git subtree add --prefix cork/ cork master [--squash]

    git subtree pull --prefix cork/ cork master [--squash]
