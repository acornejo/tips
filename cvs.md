# CVS

    export CVSROOT=/usr/local/CVS
    cvs -d $CVSROOT init
    cvs login
    cvs import -m"Project Name" Project start user
    cvs checkout project
    cvs export -DNOW project
