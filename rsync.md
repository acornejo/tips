# rsync

Copy from local to remote (use -avPz if files are compressible):

    rsync -avP Folder remotehost:
    rsync -avP ~/Folder/ remotehost:Folder
    rsync -avP --rsync-path=.bin/rsync --exclude .svn/ Site/ user@server:public_html

Copy from remote to local rsync -avP remotehost:Folder/ \~/Folder
