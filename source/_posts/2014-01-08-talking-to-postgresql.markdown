---
layout: post
title: "Talking to PostgreSQL"
date: 2014-01-08 10:03
comments: true
categories: 
---

------

PostgreSQL is a powerful object-relational database management system, provided under
a flexible BSD-style license. PostgreSQL has bindings for many programming languages
such as C, C++, Python, Java, PHP, Ruby and so on. It can be used to power anything
from simple web applications to massive databases with millions of records. 
<!--more-->

------

## Client Installation ##

If you only wish to connect to a PostgreSQL server, just install the PostgreSQL client:

```
sudo apt-get install postgresql-client
```

You then connect to the server with the following command:

```
psql -h <server> <database> <user>
```

------

## Server Installation ##

To install use the command line and type:

```
sudo apt-get install postgresql
```

If you are a beginner, pgAdmin is helpful for you. It's a handy GUI for PostgreSQL:

```
sudo apt-get install pgadmin3
```

------

## Basic Server Setup ##

To start off, we need to change the PostgresSQL postgres user password:

```
sudo -u postgres psql postgres
\password postgres
```
You then give your password when prompted and type Control-D to exit.

------

## Create Database ##

Before creation, create a user as the owner of the first database:

```
sudo -u postgres createuser -P tester
```

Then create a password for the user:

```
sudo -u postgres psql
\password tester
```

To create the first database, which we will call "mydb", simply type:

```
sudo -u postgres createdb mydb -O tester
```

Certainly, you can drop it like this:

```
sudo -u postgres dropdb mydb
```

------

## Inspect Database ##

Get help:

```
mydb=# \?
mydb=# \h
```

Show version:

```
mydb=# SELECT version();
```

Change database:

```
mydb=# \c [database]
```

Show databases:

```
mydb=# \l
```

Show tables:

```
mydb=# \dt
```

Show table columns:

```
mydb=# \d [database]
```

Read commands from file:

```
mydb=# \i [file]
```

Quit:

```
mydb=# \q
```

------

## Backup Database ##

Dump a database:

```
sudo -u postgres pg_dump [database] > [file]
```

Restore a database:

```
sudo -u postgres psql -d [database] -f [file]
```

