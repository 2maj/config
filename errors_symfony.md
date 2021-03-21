- PHP Warning: PHP Startup: Unable to load dynamic library 'pdo_mysql' (tried: /usr/lib/php/20200930/pdo_mysql (/usr/lib/php/20200930/pdo_mysql: cannot open shared object file: No such file or directory), /usr/lib/php/20200930/pdo_mysql.so (/usr/lib/php/20200930/pdo_mysql.so: undefined symbol: mysqlnd_allocator)) in Unknown on line 0 PHP Warning: PHP S
>sudo apt-get --purge remove php-common

>sudo apt-get install php-common php-mysql php-cli

-Root composer.json requires php ^7.4 but your php version (8.0.3) does not satisfy that requirement.
"require": {
        "php": "^7.4|^8.0",

- Extension DOM is required.
> sudo apt-get install php-xml
If possible sudo apt-get install php-mbstring

