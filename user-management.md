# user-management

To lock a user:

    usermod -L user

To unlock a user:

    usermod -U user

To add a user with a fixed password:

    useradd -m user
    echo "user:passwd" | chpasswd

To remove a user:

    userdel -r user

To add an existing user to an existing group:

    usermod -G group -a user

To copy the groups USER1 into USER2:

    G=$(awk -F: "{ if (\$4 ~ /$USER1/) print \$1 }" ORS=',' /etc/group | sed 's/,$//')
    usermod -G $G -a $USER2
