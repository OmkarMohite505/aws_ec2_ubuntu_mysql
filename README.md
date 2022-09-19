
# Install MySql on AWS EC2 Ubuntu OS instance and Take remote connection
<div>
  <img src="https://github.com/devicons/devicon/blob/master/icons/mysql/mysql-original-wordmark.svg" title="MySQL"  alt="MySQL" width="100" height="100"/>&emsp;&emsp;
  <img src="https://github.com/devicons/devicon/blob/master/icons/amazonwebservices/amazonwebservices-plain-wordmark.svg" title="AWS" alt="AWS" width="100" height="100"/>&nbsp;
</div>

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
mysql -u root -p
```
Then Enter password 'root' and press Enter
and now create one new user by giving following commands
```bash
CREATE USER 'user'@'%' IDENTIFIED WITH mysql_native_password BY 'user';
```
Give Permissions to user
```bash
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' WITH GRANT OPTION;
```
To list out users 
```bash
select user, host from mysql.user;
```
To delte user, Meaning :DROP USER 'username'@'host';
```bash
DROP USER 'root'@'%';
```







## Security Change needed in AWS
in AWS EC2 instance go to security group and click on Edit Inbound Rules
and add Following Rule
```bash
Mysql/Auora     3306     Anywhere from IPV4
```
and Save it
To see your OS version
```bash
cat /etc/issue
```
Now Open your MySql Workbench and in Hostname Enter your AWS EC2 instance public IP address, enter username: which is we created with name 'user' and password: 'user'
and Click on Test Connection
