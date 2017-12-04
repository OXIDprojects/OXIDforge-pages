This document describes several possibilities how to forward the URL for your OXID eShop into the source/ folder.

## Adapt your vhost

## Set a symlink

## Alter your .htaccess file

```
RewriteCond %{HTTP_HOST} .* [NC]
RewriteCond %{REQUEST_URI} !source/
RewriteRule ^(.*)$ source/$1 [L]
```
