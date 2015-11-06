# MySQL

    mysqladmin -u root password "newpass"
    mysql -u root -p
    create database dbname;
    use dbname;
    GRANT SELECT,INSERT,UPDATE,DELETE ON dbname.* to user@localhost IDENTIFIED BY "password";
    FLUSH PRIVILEGES;
    show databases;
    show tables;
    drop databasename;
    mysqldump --databases -u username -ppassword database > complete.sql
    mysqldump -u username -ppassword database -d > schema.sql
    mysqldump -u username -ppassword database -tn > data.sql
    mysqldump --add-drop-table -u username -ppassword database > complete.sql
