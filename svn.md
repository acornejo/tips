# SVN

    SVNROOT=/usr/local/SVN
    svnadmin create --fs-type=fsfs $SVNROOT
    svn import -m"Project Name" Project file://$SVNROOT/Project
    svn checkout file://$SVNROOT/Project Project
    svn checkout svn+ssh://server$SVNROOT/Project Project
    svn export file://$SVNROOT/Project Project
    svnadmin dump $SVNROOT > svn.backup
    svnadmin load $SVNROOT < svn.backup
