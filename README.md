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

