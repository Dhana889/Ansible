Installation commmand mysql Ubuntu Machine:

sudo apt update
sudo apt install mysql-server
sudo systemctl enable mysql.service
sudo systemctl start mysql.service
systemctl status mysql.service

Change mysql passwqord
sudo mysql
mysql> ALTER USER root@localhost 
IDENTIFIED WITH mysql_native_password  
BY '<YOUR_PASSWORD>';

to login: 
mysql -u root -p

To secure MySQL installation:
sudo mysql_secure_installation

Installation commmand mysql Centos Machine:

 rpm -Uvh https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm
yum --enablerepo=mysql80-community install mysql-community-server
 sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
yum --enablerepo=mysql80-community install mysql-community-server
 yum install mysql
yum install mysql-server
yum -y install mysql-community-server
 service mysqld  status
 service mysqld  start
service mysqld  status

Change mysql passwqord
  grep "A temporary password" /var/log/mysqld.log
  mysql_secure_installation

Database and table create:
mysql -u root -p
show databases;
create database kritika;
use devops;
create table tblEmployee1(Employee_first_name varchar(500) NOT null,Employee_last_name varchar(500) NOT null);
INSERT INTO tblEmployee1 (employee_first_name, employee_last_name) values ("Dhana","Sekaran");

Aws cli install and configure
curl “https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip” -o "awscliv2.zip"
 yum install unzip
 unzip awscliv2.zip
 ./aws/install
 aws configure

Ansible install
 yum install epel-release
 yum install ansible

vi main.yaml:

---
 - name: this is my first playbook
   hosts: localhost
   tasks:
     - name: Take Mysql backup
       shell: mysqldump -u root --password="yourpassword"  devops  tblEmployee1 > /tmp/dump3.sql
     - name: Push Mysql backup to s3 bucket
       shell: aws s3 cp  /tmp/dump3.sql s3://mysql-backup-909
       
  ansible-playbook main.yaml
 
