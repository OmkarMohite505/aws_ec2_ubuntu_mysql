
# Install MySql on AWS EC2 Ubuntu OS instance and Take remote connection


## So give these command one by one on terminal to install MySql

```bash
  sudo apt update
```
```bash
  sudo apt install mysql-server
```
To see status
```bash
  sudo service mysql status
```
If the server is not running correctly, you can type the following command to start it:
```bash
  sudo service mysql restart
```





## Configuration
```bash
cd /
```
```bash
cd etc/mysql/mysql.conf.d/mysqld.cnf
```
```bash
nano mysqld.conf
```
find bind-address line and change it to following
```bash
bind-address = 0.0.0.0
```
```bash
sudo service mysql restart
```
```bash
CREATE USER 'user'@'%' IDENTIFIED WITH mysql_native_password BY 'user';
```
```bash
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' WITH GRANT OPTION;
```







## Security Change needed in AWS
in AWS EC2 instance go to security group and click on Edit Inbound Rules
and add Following Rule
```bash
Mysql/Auora     3306     Anywhere from IPV4
```
and Save it