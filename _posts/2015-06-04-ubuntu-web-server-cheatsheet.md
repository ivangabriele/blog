---
layout: post
title:  "[Ubuntu] Web Server Cheatsheet"
date:   2015-06-04
banner_image: Ubuntu.jpg
tags: [Apache, Bash, Debian, MySQL, PHP, Ubuntu]
---

I created and will udpdate this list in relation to my own usage. Just tell me if you think something is missing.

<!--more-->

## Server First Set Up

### Installation of Apache, PHP and MySQL

    sudo apt-get update
    sudo apt-get upgrade
    sudo apt-get install apache2 libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql php5-mysql

### Set up Apache virtuals hosts

    sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf
    sudo vim /etc/apache2/sites-available/example.com.conf

Example :

    <VirtualHost *:80>
        ServerAdmin admin@example.com
        ServerName example.com
        ServerAlias www.example.com
        DocumentRoot /var/www/example.com
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>

And :

    sudo a2dissite 000-default
    sudo a2ensite example.com
    sudo service apache2 reload

### Set up domain DNS records

    @ 10800 IN A 12.34.56.78

## Linux bash common operations

### Extract a .tar.gz

    tar -zxvf file.tar.gz

## MySQL common operations

### List MySQL users

    SELECT User, Host, Password FROM mysql.user;

### Create new MySQL user

    CREATE USER 'jeffrey'@'localhost' IDENTIFIED BY 'mypass';

### Change MySQL user password

    SET PASSWORD FOR 'bob'@'%.example.org' = PASSWORD('cleartext password');

### Delete MySQL user

    DROP USER 'jeffrey'@'localhost';

### Create MySQL database

    CREATE DATABASE dbname CHARACTER SET utf8 COLLATE utf8_general_ci;

### Grant MySQL privileges

    GRANT ALL ON db1.* TO 'jeffrey'@'localhost';
