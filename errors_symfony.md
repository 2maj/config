- PHP Warning: PHP Startup: Unable to load dynamic library 'pdo_mysql' (tried: /usr/lib/php/20200930/pdo_mysql (/usr/lib/php/20200930/pdo_mysql: cannot open shared object file: No such file or directory), /usr/lib/php/20200930/pdo_mysql.so (/usr/lib/php/20200930/pdo_mysql.so: undefined symbol: mysqlnd_allocator)) in Unknown on line 0 PHP Warning: PHP S
>sudo apt-get --purge remove php-common

>sudo apt-get install php-common php-mysql php-cli
