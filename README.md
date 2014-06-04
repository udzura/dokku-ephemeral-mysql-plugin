dokku-ephemeral-mysql-plugin
============================

Dokku plugin to create and link to an ephemeral mysql container

## Install

```bash
cd /var/lib/dokku/plugins
git clone https://github.com/udzura/dokku-ephemeral-mysql-plugin.git ephemeral_mysql
dokku plugins-insall ephemeral_mysql
```

## Commands

```
    ephemeral_mysql:create <mysql_app> Create a ephemeral MySQL container
    ephemeral_mysql:delete <mysql_app> Delete specified MySQL container
    ephemeral_mysql:info <mysql_app> Display container informations
    ephemeral_mysql:link <main_app> <mysql_app> Link an app to a MySQL container
    ephemeral_mysql:logs <mysql_app> Display last logs from MySQL container
```

## Simple usage

```bash
ssh -t dokku@server ephemeral_mysql:create sample
git remote add dokku dokku@server:sample
git push dokku master
# Automatically linked
ssh -t dokku@server ephemeral_mysql:info sample

Host:          172.17.0.9
    Internal port: 3306
    Public port:   49214
    User name:     root
    Password:      docker
    DB name:       sample

ssh -t dokku@server config sample

=== sample config vars ===
DATABASE_URL: mysql://root:docker@172.17.0.9:3306/sample
MYSQL_URL:    mysql://root:docker@172.17.0.9:3306/sample
Connection to dokku@server closed.

```

## See also

* MariaDB Plugin https://github.com/Kloadut/dokku-md-plugin
* Redis Plugin https://github.com/jezdez/dokku-redis-plugin
