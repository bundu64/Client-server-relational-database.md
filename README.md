# Client-server-relational-database.md
### Client-Server Architecture With MYSQL

#### Setup two instances of mysql

mysql server

mysql client

### Mysql server uses TCP Port 3306 by default.

### To Create a new rule in the security group, allow connections on port 3306 and allow the client private ip address in the security group.

### Launch the DB Server

### Run this script on the Database Server

sudo mysql_secure_installation 
sudo mysql

### Allow client private ip address in the inbound rules while selecting mysql

### Run this script on DB Server

CREATE USER 'remote_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';

CREATE DATABASE test_db;

GRANT ALL ON test_db.* TO 'remote_user'@'%' WITH GRANT OPTION;

FLUSH PRIVILEGES;

### Configure MySQL server to allow connections from remote hosts

sudo vi /etc/mysql/mysql.conf.d/mysqld.cnf

### Locate the bind address and Replace ‘127.0.0.1’ to ‘0.0.0.0’

### From mysql client Linux Server connect remotely to mysql server Database Engine without using SSH

sudo mysql -u remote_user -h 172.31.47.133 (ip address of database server) -p

Show databases;
