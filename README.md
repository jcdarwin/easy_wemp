# Easy WEMP #

WEMP = Windows NgInx MySql Php

*Easy WEMP provide a web development environment which include NgInx as HTTP server, MySQL as database server, and PHP as server-side scripting language.*

*It's primary goal is to give user a easy service management on their windows desktop.*

## Introduction ##

These are simply my notes on getting Yann Le Moign's [Easy WEMP project](https://projects.javatic.fr/p/easy-wemp/) working on my Windows machine.

Unfortunately the Easy WEMP installable contains download paths for a number of components (PHP, MySQL, MySQL Workbench) that don't resolve correctly.
However, it still provides a useful starting point, and it's pretty straight-forward to add the missing components.

## Downloads ##

Easy WEMP is available at [https://projects.javatic.fr/p/easy-wemp/]()

* Download [Easy_WEMP-1.13-win32.exe](https://projects.javatic.fr/p/easy-wemp/downloads/get/Easy_WEMP-1.13-win32.exe)
* Download [php-5.4.9-Win32-VC9-x86.zip](http://windows.php.net/downloads/releases/php-5.4.9-Win32-VC9-x86.zip)
* Download [mysql-workbench-gpl-5.2.44-win32-noinstall.zip](http://dev.mysql.com/downloads/mirror.php?id=410033)
* Download [mysql-noinstall-5.1.47-win32.zip](https://projects.javatic.fr/p/easy-wemp/downloads/3/)

## Installation ##

### Easy WEMP ###
* Run `Easy_WEMP-1.13-win32.exe`
* Deselect PHP, MySQL, and MySQL Workbench (as the internal download URLs do not correctly resolve)
* Continue, such that Easy WEMP is installed at c:\ewemp

### PHP ###
* Extract `php-5.4.9-Win32-VC9-x86.zip` to:

        c:\ewemp\php-5.4.9-Win32-VC9-x86

* Copy `c:\ewemp\php-5.4.9-Win32-VC9-x86\php-development.ini` to `php.ini`, and tweak accordingly.

### MySQL ###
* Extract `mysql-noinstall-5.1.47-win32.zip` to:

        c:\ewemp\mysql-noinstall-5.1.47-win32

* Copy one of the following to `my.ini` and tweak accordingly:

        my-huge.ini
        my-large.ini
        my-medium.ini
        my-small.ini

### MySQL Workbench ###
* Extract `mysql-workbench-gpl-5.2.44-win32-noinstall.zip` to:

        c:\ewemp\mysql-workbench-gpl-5.2.44-win32-noinstall

### Correct the Easy WEMP ini file ###
* Edit `c:\ewemp\ewemp.ini` as follows (example settings can be found in `c:\ewemp\README.txt`):

        nginx=nginx-0.8.52
        php=php-5.4.9-Win32-VC9-x86
        mysql=mysql-noinstall-5.1.47-win32
        mysqlworkbench=mysql-workbench-gpl-5.2.44-win32-noinstall
        [manage]
        nginx=true
        php=true
        mysql=true
        mysqlworkbench=true
        [nginx]
        exec=/nginx.exe
        sites=/html
        config=/conf
        logs=/logs
        [php]
        exec=/php-cgi.exe
        fastcgi-bindaddress=localhost
        fastcgi-bindport=9000
        [mysql]
        exec=/bin/mysqld.exe
        config=/my.ini
        clientExec=/bin/mysql.exe
        [mysqlworkbench]
        exec=/MySQLWorkbench.exe
        [global]
        autostartdaemons=true

### Start it up ###
* Create `info.php` in:

        C:\ewemp\nginx-0.8.52\html

* Include the following in `info.php`:

        <?php 
        phpinfo();
        ?> 

* Double-click:

        C:\ewemp\ewemp.exe

* Navigate to:

        http://localhost/info.php

Bingo!