# Config Apache

##Config site 
**Following handling will be execute as sudo**
- Create file my_web_site.conf in your apache folder :
        - sudo touch /etc/apache2/sites-available/my_web_site.conf
- Set the content with the next code 

>       <VirtualHost *:80>
                ServerAdmin adjimahamat@gmail.com

                ServerName  my-domain.com
                ServerAlias *.my-domaine.com
                DocumentRoot /link/to/my/project/site/public
                <Directory /link/to/my/project/site/public>
                        AllowOverride None
                        Order Allow,Deny
                        Allow from All

                        <IfModule mod_rewrite.c>
                                Options -MultiViews
                                RewriteEngine On

                                RewriteCond %{REQUEST_FILENAME} !-f
                                RewriteRule ^(.*)$ index.php [QSA,L]
                        </IfModule>
                </Directory>

                ErrorLog /var/log/apache2/my-domain.com_error.log
                CustomLog /var/log/apache2/my-domain.com_access.log combined
        </VirtualHost>
- 
> chown -R votre-usager-ssh /var/www/html
> chown -R votre-usager-ssh /var/www/my_web_site
> chgrp -R www-data /var/www/my_web_site

#Run your web site
>a2ensite 001-my_web_site.conf
>service apache2 restart

#To finish you need redirect your domain name to your server vps :
- Connect on your account register domain name
- Create a redirection from your-domain-name.com to your-server-name.net



NOW enjoy your site