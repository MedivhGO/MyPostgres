Ubuntu14.04  Denpendcy
=====================================

```
sudo apt-get install build-essential libreadline-dev zlib1g-dev flex bison libxml2-dev libxslt-dev libssl-dev
```

Compile PostgreSQL Short Version 
=====================================

```
./configure
make
su
make install
adduser postgres
mkdir /usr/local/pgsql/data
chown postgres /usr/local/pgsql/data
su - postgres
/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
/usr/local/pgsql/bin/pg_ctl -D /usr/local/pgsql/data -l logfile start
/usr/local/pgsql/bin/createdb test
/usr/local/pgsql/bin/psql test
```

```
./configure  --enable-debug CFLAGS="-O0 -g" # 添加调试信息
make -sj # 并发编译
make install -sj # 并发安装
```

Debug Workflow
=====================================

```
su postgres

/usr/local/pgsql/bin/psql -p 2345 # 修改过端口号,如果没修改过,可不写

select pg_backend_pid(); # 得到当前客户端postgres分配的进程号

sudo gdb -p portnumber

```

Change Port 
=====================================

```
vim /usr/local/pgsql/data/postgresql.conf 
```

Remove PostgreSQL
=====================================

```
make uninstall # 卸载postgres
make clean # 清理安装文件
```


PostgreSQL Database Management System
=====================================

This directory contains the source code distribution of the PostgreSQL
database management system.

PostgreSQL is an advanced object-relational database management system
that supports an extended subset of the SQL standard, including
transactions, foreign keys, subqueries, triggers, user-defined types
and functions.  This distribution also contains C language bindings.

PostgreSQL has many language interfaces, many of which are listed here:

	https://www.postgresql.org/download/

See the file INSTALL for instructions on how to build and install
PostgreSQL.  That file also lists supported operating systems and
hardware platforms and contains information regarding any other
software packages that are required to build or run the PostgreSQL
system.  Copyright and license information can be found in the
file COPYRIGHT.  A comprehensive documentation set is included in this
distribution; it can be read as described in the installation
instructions.

The latest version of this software may be obtained at
https://www.postgresql.org/download/.  For more information look at our
web site located at https://www.postgresql.org/.
