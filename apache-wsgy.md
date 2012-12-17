# Configuracion de Apache con WSGI

## Configuracion de vHost para Tree.io en httpd.conf con disparador de aplicacion automagico

```text
<VirtualHost 10.96.18.139:80>
    DocumentRoot /var/www/treeio
#    ErrorLog /var/www/treeio/logs/apache_error.log
#    CustomLog /var/www/treeio/logs/apache_access.log combined

    WSGIScriptAlias / /var/www/treeio/wsgi.py

    Alias /robots.txt /var/www/treeio/static/robots.txt
    Alias /favicon.ico /var/www/treeio/static/favicon.ico
    Alias /media/ /var/www/treeio/static/media/
    AliasMatch ^/([^/]*\.css) /var/www/treeio/static/styles/$1

    <Directory /var/www/treeio>
        Order deny,allow
        Allow from all
    </Directory>

    <Directory /var/www/treeio/media>
        Order deny,allow
        Allow from all
    </Directory>

    <Directory /var/www/treeio/apache>
        Order deny,allow
        Allow from all
    </Directory>
</VirtualHost>

```
