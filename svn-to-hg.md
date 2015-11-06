# SVN-to-HG

First create a directory to store your mercurial repository and make it
your working directory.

Then execute the following to convert:

    source_repo=file://$HOME/PATH_TO_REPO
    repos=`svn ls $source_repo | tr -d \/ | tr '\n' ' '`
    for repo in $repos; do
        hgimportsvn $source_repo/$repo
        cd $repo
        hgpullsvn
        hg update
        cd ..
    done
    find . -name .svn -exec rm -fR {} \;

In case you want to get rid of the default preferences:

    find . -name .hgignore -exec rm -f {} \;
