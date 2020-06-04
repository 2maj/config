#Config SQLite in Laravel
##Create database
- Create file database/seeds/database.sqlite

##config env
- In file .env : 
>DB_CONNECTION=sqlite

- **Important !** chech in your php.ini if sqlite is enable like :
>extension=pdo_sqlite

#Launch DB
- Run the next cmd to allow to Laravel to init your Database when existing db :
>php artisan migrate
- **Here no db exist** : you can create your tables
>php artisan make:model city -m




##Sources :
- https://www.youtube.com/watch?v=c2cRW72U6QM