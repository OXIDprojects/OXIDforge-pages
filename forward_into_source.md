This document describes several possibilities how to forward the URL for your OXID eShop into the source/ folder.

## Adapt your vhost

similar to https://mysqldumper.jira.com/wiki/spaces/OTC/pages/11665436/Installing+manually

## Set a symlink

## Alter your .htaccess file

```
RewriteCond %{HTTP_HOST} .* [NC]
RewriteCond %{REQUEST_URI} !source/
RewriteRule ^(.*)$ source/$1 [L]
```
