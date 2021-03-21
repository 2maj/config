#Configuration Mysql

##Installation
> sudo apt-get install mysql-server

#Installation php
> sudo apt-get install php-mysql
> sudo service apache2 restart

##Settings
This utility prompts you to define the mysql root password and other security-related
 options, including removing remote access to the root user and setting the root
 password.
> sudo mysql_secure_installation utility

# Launch
With your preview password saved, you can log in mysql.
If you used sudo during your installation 
>sudo mysql -u root -p
else
>mysql -u root -p

#Create new user
> create user 'admin'@'localhost' identified by 'Admin1234-';

#Access right
> GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
> FLUSH PRIVILEGES;


Now enjoy !
