# Set-up-Virtual-Hosts-on-macOS-Catalina in Apache in Sites folder

## Allow the vhosts configuration from the Apache configuration file httpd.conf

Open the httpd.conf
<pre>
sudo nano /etc/apache2/httpd.conf
</pre>

Search for ‘vhosts‘ and uncomment the  these line

<pre>
LoadModule include_module libexec/apache2/mod_include.so
LoadModule rewrite_module libexec/apache2/mod_rewrite.so
</pre>

Edit the vhosts.conf file

Open this file to add in the virtual host.

sudo nano /etc/apache2/extra/httpd-vhosts.conf


```html
<VirtualHost *:80>
    ServerName local.mysite.com
    ServerAlias local.mysite.com
    DocumentRoot "/Users/manojkumar/Sites/mysite.com"
    <Directory "/Users/manojkumar/Sites/mysite.com">
         Options Indexes FollowSymLinks Includes execCGI
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>`
```


## Map Your IP address to localhost

sudo nano /etc/hosts

<pre>
sudo nano /etc/hosts
</pre>

Add your virtual host 
<pre>
127.0.0.1 local.mysite.com
</pre>

Restart Apache

<pre>
Restart Apache
</pre>

## Losing Localhost then

Edit
<pre>
sudo nano /etc/apache2/extra/httpd-vhosts.conf
</pre>

Add in:

```html
<VirtualHost *:80>
ServerName localhost
DocumentRoot "/Users/manojkumar/Sites"
<Directory "/Users/manojkumar/Sites">
        Options Indexes FollowSymLinks Includes execCGI
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>`
```

Restart Apache

```yaml
sudo apachectl restart
```
