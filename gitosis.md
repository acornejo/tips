# Gitosis

Install:

    apt-get install gitosis

Change gitosis location (optional):

    usermod -m -d /storage/gitosis gitosis

Create gitosis repo:

    sudo -H -u gitosis gitosis-init < ~/.ssh/id_rsa.pub

Configure gitosis for a new repo called myproject:

    git clone gitosis@localhost:gitosis-admin.git
    cd gitosis-admin
    cat << EOF >> gitosis.conf

    [group myteam]
    members = user@localhost
    # To allow access through the git:// protocol, uncomment the following
    # daemon = yes
    # To allow access through gitweb, uncomment the following
    # gitweb = yes
    writable = myproject
    EOF

Save changes to gitosis-admin:

    git commit -a -m "Added myproject to gitosis"
    git push

Setup your (existing) to push to gitosis:

    cd myproject
    git init
    git add .
    git commit -a -m "Initial import"
    git remote add origin gitosis@localhost:myproject.git
    git push origin master
    git config branch.master.remote origin
    git config branch.master.merge refs/heads/master

Give alice permission to your repo:

    cd gitosis-admin
    cp ~/alice.pub keydir/
    git add keydir/alice.pub

    # change your gitosis.conf
      [group myteam]
    - members = user@localhost
    + members = user@localhost alice
