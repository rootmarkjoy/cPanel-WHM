# cPanel-WHM
cPanel/WHM Documentation

The cPanel accounts are created using a primary domain. All primary domains on the hosting account use “public_html” directory for all its website files and data. The sub-directories inside the public_html directory is occupied by the addon domains. 
The primary domain can also be setup to use a sub-directory inside public_html directory instead of public_html itself. Follow the below steps to change the document root of your primary domain in cPanel account. Please note that, you will need to have root SSH access to perform these steps.

1) Connect to your server via SSH as root user. You may follow the tutorial below, if you are using a Windows system to connect to your server via SSH. 
This tutorial explains how to use “Putty”, SSH client software to access server.

*** Replace the “username” with your cPanel account username and “domain.com” with your primary domain name and “subdir” with your new directory. 

Find the following two lines in this file:-

```sh
vi /etc/apache2/conf/httpd.conf
```

Change the path as per requirement for example.com and www.example.com

Made changes in configuration file, like "/var/cpanel/userdata/example/"

```sh
[root@flawless coretrade]# vi example.com
[root@flawless coretrade]# vi example.com_SSL
```

Run the following scripts to update the user data cache and rebuild apache configuration file:-

```sh
[root@flawless config]# /scripts/updateuserdatacache
[root@flawless config]# /scripts/rebuildhttpdconf
Built /etc/apache2/conf/httpd.conf OK
```

Restart Apache server to load changes:-

```sh
[root@flawless config]# service httpd restart
```
