---
layout: post
title:  "[Ubuntu] How to completely uninstall MySQL Server ?"
date:   2014-11-28
banner_image: Ubuntu.jpg
tags: [Bash, Debian, MySQL, Ubuntu]
---

### Clean uninstall

    sudo apt-get --purge remove mysql-client mysql-server mysql-common
    sudo apt-get autoremove

### Configuration directory deletion

    sudo rm -rf /etc/mysql

### Databases deletion

    sudo rm -rf /var/lib/mysql
