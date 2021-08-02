# **Install `MySQL 5.7` on `Ubuntu 14.04 LTS`**

```
$ echo 'deb http://repo.mysql.com/apt/ubuntu/ trusty mysql-5.7-dmr' | sudo tee -a /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get install mysql-server-5.7
...
$ mysql --version
mysql  Ver 14.14 Distrib 5.7.8-rc, for Linux (x86_64) using  EditLine wrapper
$
```

**Dont forget your `root` password**

Connect to your MySQL server:

```
$ mysql -hlocalhost -uroot -p
Password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 42
Server version: 5.7.8-rc MySQL Community Server (GPL)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
mysql> quit
Bye
$
```

if you have some issues to upgrade to 5.7, don’t hesitate to cleanup your server of any MySQL packages:
```
sudo apt-get remove --purge mysql-server mysql-client mysql-common
```

If you had before `MySQL 5.5` installed, please run these 2 commands after the installation of the `version 5.7`:

```
$ mysql_upgrade -u root -p
Password: 
$ sudo service mysql restart
```

**Start Mysql**
```
$ service mysql start
 * MySQL Community Server 5.7.8-rc is started
$
$ mysql -uroot -p
Enter password:
```

## **How to import a SQL dump**
```
$ echo "CREATE DATABASE hbtn_0d_tvshows;" | mysql -uroot -p
Enter password: 
$ curl "https://s3.amazonaws.com/intranet-projects-files/holbertonschool-higher-level_programming+/274/hbtn_0d_tvshows.sql" -s | mysql -uroot -p hbtn_0d_tvshows
Enter password: 
$ echo "SELECT * FROM tv_genres" | mysql -uroot -p hbtn_0d_tvshows
Enter password: 
id  name
1   Drama
2   Mystery
3   Adventure
4   Fantasy
5   Comedy
6   Crime
7   Suspense
8   Thriller
$
```
