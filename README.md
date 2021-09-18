README
======

MySQL
-----

```bash
$ cd mysql
$ docker-compose up -d
$ docker-compose exec mysql bash
root@58c866b5e15f:/# mysql -ualpha -phinex
mysql: [Warning] Using a password on the command line interface can be insecure.
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 6
Server version: 5.7.34 MySQL Community Server (GPL)

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show status like 'Threads_connected';
+-------------------+-------+
| Variable_name     | Value |
+-------------------+-------+
| Threads_cached    | 1     |
| Threads_connected | 3     |
| Threads_created   | 4     |
| Threads_running   | 1     |
+-------------------+-------+
4 rows in set (0.00 sec)
```

Check `Threads_connected` value.


HikariCP
--------

```bash
$ cd pools/hikari
$ ./gradlew bootRun
```

After startup, check MySQL `Threads_connected` value and wait 35 seconds to check it again.

Threads connected closed by MySQL.

```bash
$ ./gradlew bootRun -Pprofile=keepalive
```

HikariCP could keep connected threads alive.


Druid
-----

Change directory to pools/druid, and use commands as above.
