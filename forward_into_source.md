This document describes several possibilities how to forward the URL for your OXID eShop into the source/ folder.

## Adapt your vhost

similar to https://mysqldumper.jira.com/wiki/spaces/OTC/pages/11665436/Installing+manually

## Set a symlink

## Create a .htaccess file 

```
<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{HTTP_HOST} .* [NC]
    RewriteCond %{REQUEST_URI} !source/
    RewriteRule ^(.*)$ source/$1 [L]
</IfModule>
```
Additionally, you have to add a line to config.inc.php in source folder:
```
$_SERVER['SCRIPT_NAME'] = str_replace('/source', '', $_SERVER['SCRIPT_NAME']);
```
