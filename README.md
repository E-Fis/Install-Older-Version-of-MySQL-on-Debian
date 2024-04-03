# Install-Older-Version-of-MySQL-on-Debian
The following steps worked to install MySQL 5.1.73 on Debion x86_64

Credits to the author:Bo Lechnowsky, CEO of ameriDroid.com


1. cd /usr/local -->	The location where MySQL should be installed
2. wget https://downloads.mysql.com/archives/get/p/23/file/mysql-5.1.73-linux-glibc2.12-x86_64.tar.gz --> If this returns an error, it is because this file has been moved or removed from MySQL's site (use a web browser to find the archived files on the MySQL site and copy the link to the version you want)
3. groupadd mysql -->	If this returns an error, this step wasn't needed
4. useradd -g mysql mysql -->	If this returns an error, this step wasn't needed
5. tar -xvf mysql*.tar.gz -->	Extracts MySQL into the current directory
6. rm mysql-*.gz -->	Removes the compressed file that is no longer needed
7. mv mysql-* mysql -->	Renames the long MySQL directory name to the short version
8. chown root:root mysql -->	Changes the permissions on the mysql directory to the correct permissions
9. cd mysql -->	Goes into the mysql directory
10. chown -R mysql:mysql * -->	Changes permissions on all the files in the mysql directory to the mysql user and the mysql group
11. apt install libaio1 -->	May already be installed, but just to make sure
12. scripts/mysql_install_db --user=mysql -->	Installs MySQL
13. chown -R root . -->	Changes permissions on the files in the MySQL directory
14. chown -R mysql data -->	Changes permissions on the MySQL data directory
15. cp support-files/my-medium.cnf /etc/my.cnf -->	Copies the configuration file to the correct location
16. bin/mysqld_safe --user=mysql & cp support-files/mysql.server /etc/init.d/mysql.server -->	Starts MySQL server and copies the autostart file to the correct location
17. bin/mysqladmin -u root password 'pswd' -->	Change 'pswd' to the MySQL root password - This will be referred to as the MySQL root password from now on
18. /etc/init.d/mysql.server start -->	Starts MySQL server
19. /etc/init.d/mysql.server stop -->	Stops MySQL server
20. update-rc.d -f mysql.server defaults -->	Enables MySQL to start when computer is rebooted
21. ln -s /usr/local/mysql/bin/mysql /usr/local/bin/mysql -->	Adds MySQL to the system path
22. apt install libncursesw5 -->	Installs a library needed by MySQL
