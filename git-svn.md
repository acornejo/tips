# git-svn

Install git-svn:

    apt-get install git-svn

Checkout the SVN repository into your local git repo:

    git svn clone http://repourl/project
    cd project

Commit your changes using git (as usual):

    git ci -a -m "commit message."

Update your local git repo from the remote SVN repository:

    git svn rebase

Send your git commits upstream to the SVN repository:

    git svn dcommit

Export your current git repo to a clean SVN (this assumes you are in a
folder which is already a git repository with some non empty history):

    git config svn-remote.svn.url svn-remote.svn.url https://repourl/project
    git config svn-remote.svn.fetch :refs/remotes/git-svn
    git svn fetch
    git rebase remotes/git-svn
    git svn dcommit
