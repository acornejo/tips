# SSH-Restrict

To restrict to a given set of users, first edit the file
/etc/ssh/sshd\_config and add the following line:

    AllowUsers user1 user2 .. usern

For added security, disable all login methods except public key:

    UsePAM no
    ChallengeResponseAuthentication no
    PasswordAuthentication no
