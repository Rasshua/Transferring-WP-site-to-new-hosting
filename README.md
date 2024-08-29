# Transferring WP site to new hosting
User manual how to transfer WP website from localhost to permanent internet hosting

## 1. Introducing

Each WordPress website consists of two main components:

1. Site files, located in dedicated directory of server (mainly contains .php code, configurations, nedia)
2. Database (SQL database - MySQL or MariaDB or some another compatible one)

So, during the transfering process it is necessary to perform the following steps:

1. Copy site files into dedicated directory at permanent hosting
2. Copy the dump of database into the server at permanent hosting
3. Change the site configuration file(s) according to new hosting parameters
4. Modify some records in the database

## 2. Prerequisites

For the old hosting the user must have the following:

1. Ability to make a copy of all site files on the local PC
2. Ability to create the dump of WP database (for example, via DBeaver or phpMyAdmin)

For the new hosting the user will need:

1. Access to site files in the dedicated directory (add, modify, and delete files)
2. Ability to create new database and to link it with desired site name
3. Ability to import the dump of WP database to new database (for example, via phpMyAdmin)
4. Ability to perform SQL queries on new database (for example, via phpMyAdmin)

## 3. Copying the site from old hosting to the local machine

### 3.1. Creating a full copy of the site files on the local machine

1. Logging in on the old hosting via SSH:
```console
ssh <username>@your_local_server_name
```
2. Identifying the directory, where site files are located:
```console
cd /var/www/site_name
ls -al
```
In the given example, web server operates under Apache and, therefore, all site files are located in _/var/www/_ directory. For other kind of servers the location of site files may be specified separately.

This is an example how the directory with WP site files looks like:
```console
total 304
-rw-r--r--  1 u934128498 o1005197286   405 Feb  6  2020 index.php
-rw-r--r--  1 u934128498 o1005197286 19915 Aug 27 13:21 license.txt
-rw-r--r--  1 u934128498 o1005197286  7409 Aug 27 13:21 readme.html
-rw-r--r--  1 u934128498 o1005197286  7387 Feb 13  2024 wp-activate.php
drwxr-xr-x  9 u934128498 o1005197286  4096 May  7 15:52 wp-admin
-rw-r--r--  1 u934128498 o1005197286   351 Feb  6  2020 wp-blog-header.php
-rw-r--r--  1 u934128498 o1005197286  2323 Jun 14  2023 wp-comments-post.php
-rw-r--r--  1 u934128498 o1005197286  3406 Aug 27 19:58 wp-config.php
-rw-r--r--  1 u934128498 o1005197286  3033 Jul 17 12:55 wp-config-sample.php
drwxr-xr-x  9 u934128498 o1005197286  4096 Aug 27 19:59 wp-content
-rw-r--r--  1 u934128498 o1005197286  5638 May 30  2023 wp-cron.php
drwxr-xr-x 30 u934128498 o1005197286 12288 Jul 17 12:55 wp-includes
-rw-r--r--  1 u934128498 o1005197286  2502 Nov 26  2022 wp-links-opml.php
-rw-r--r--  1 u934128498 o1005197286  3937 Jul 17 12:55 wp-load.php
-rw-r--r--  1 u934128498 o1005197286 51238 Jul 17 12:55 wp-login.php
-rw-r--r--  1 u934128498 o1005197286  8525 Sep 16  2023 wp-mail.php
-rw-r--r--  1 u934128498 o1005197286 28774 Jul 17 12:55 wp-settings.php
-rw-r--r--  1 u934128498 o1005197286 34385 Jun 19  2023 wp-signup.php
-rw-r--r--  1 u934128498 o1005197286  4885 Jun 22  2023 wp-trackback.php
-rw-r--r--  1 u934128498 o1005197286  3246 Mar  2 13:49 xmlrpc.php
```

3. Create .tar archive for all site files and subdirectories:
```console
cd <site_directory>
tar -cvf <site-name>.tar ./
```

4. Download the .tar archive to the local machine (for example, via WinSCP, Filezilla, etc)

This is the screenshot of WinSCP work:

![WinSCP](https://github.com/Rasshua/Transferring-WP-site-to-new-hosting/blob/main/assets/winscp-tar-downloading.png)

### 3.2. Creating a database dump on the local machine

1.  Connect to the database on the old site histing via appropriate tool (DBeaver, phpMyAdmin etc)

In the given exanple, we are connecting to MariaDB database "wp_db" on the virtual machine via DBeaver. From the web server perspective, the database is located on localhost, and we are connecting to the server via SSH.

Connection details look like this:

![DBeaver-main](https://github.com/Rasshua/Transferring-WP-site-to-new-hosting/blob/main/assets/dbeaver-main.png)

![DBeaver-SSH](https://github.com/Rasshua/Transferring-WP-site-to-new-hosting/blob/main/assets/dbeaver-ssh.png)

2. Make the dump of database on the local machine

![DBeaver-dump](https://github.com/Rasshua/Transferring-WP-site-to-new-hosting/blob/main/assets/dbeaver-dump.png)

Select all tables in the database, and then save the file .sql on the local machine.

![Dump-wp_db](https://github.com/Rasshua/Transferring-WP-site-to-new-hosting/blob/main/assets/dump-wp_db.png)

## 4. Copying the site from the local machine to new hosting






