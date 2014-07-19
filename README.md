pg_mongo_benchmark
==================

This is a tool which can be use for benchmark the PostgreSQL (JSONB) and MongoDB (BSON)

Introduction
-------------

This is a benchmarking tool which can be use for benchmark the mongoDB 2.6 and postgreSQL 9.4 database with json data.
This tool populate amount of data mention json_rows variable in pg_mongo_benchmark.sh and does following benchmarking:
* Data loading benchmark using mongoimport and copy command of PostgreSQL.
* Data loading using mongo insert and PostgreSQL insert.
* Benchmarking of 4 selects in Mongo and PostgreSQL and produces the result as average time taken running those SQL.

Requirements
------------

1. This tool made to be run on CentOS 6.4 or later.
2. Run this script on separate CentOS server from where you have access to running MongoDB server and PostgreSQL Server.

To use this tool, set following environment Variables in pg_mongo_benchmark.sh:
1. PostgreSQL Variables:
 <code>  PGHOME=/usr/pgsql-9.4    # Installation location of PostgreSQL binaries.
   PGHOST="172.17.0.2"      # Hostname/IP address of PostgreSQL
   PGPORT="5432"            # Port number on which PostgreSQL is running.
   PGUSER="postgres"        # PostgreSQL database username.
   PGPASSWORD="postgres"    # PostgreSQL database users password.
   PGBIN=/usr/pgsql-9.4/bin # PostgreSQL binary location.
</code>
2. MongoDB Variables:
<code>
   MONGO="/usr/bin/mongo"             # Complete path of mongo Command binary
   MONGOIMPORT="/usr/bin/mongoimport" # complete path of mongoimport binary
   MONGOHOST="172.17.0.3"             # Hostname/IP address of MongoDB
   MONGOPORT="27017"                  # Port number on which MongoDB is running.
   MONGOUSER="mongo"                  # Mongo database username
   MONGOPASSWORD="mongo"              # MongoDB database username's password
   MONGODBNAME="benchmark"            # mongoDB database name.
</code>
To create userAdmin in MongoDB user can use following command on MongoDB server:
   mongo benchmark
   > db.createUser({ user: "mongo",
                     pwd: "mongo",
                     roles:[{ role: "userAdmin",
                              db: "benchmark"
                            }]
                    })


To create super user in postgresql, user can use following command:
  CREATE USER postgres
  For creating user in PostgreSQL, user can use CREATE USER command.
   http://www.postgresql.org/docs/9.4/static/sql-createuser.html

Recommended modules
--------------------
  Following package will be require on server where script will resides:
  1. mongodb-org-2.6.3-1.x86_64
  2. postgresql94-9.4beta1-1PGDG.rhel6.x86_64
  3. bc-1.06.95-1.el6.x86_64

Installation
------------
