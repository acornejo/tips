# git-submodules

To add a submodule to an existing project:

    git submodule add git@${modulehost}:${modulepath} ${modulename}

To remove a submodule form a project:

    git submodule deinit ${modulename}
    git rm ${modulename}

To pull the submodules of a project you checked out:

    git submodule update --init

To update the submodules in a project:

    git submodule foreach git pull origin master
