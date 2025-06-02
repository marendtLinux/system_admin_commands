### Basics

show databases on the server
~~~~sql
SHOW DATABASES
~~~~


Use a specific database
~~~~sql
USE <database>;
~~~~


show selected database
~~~~sql
SELECT DATABASE();
~~~~


create a new Database
~~~~sql
CREATE DATABASE <database_name>
~~~~

delete a database
~~~~sql
DROP DATABASE <database_name>
~~~~


# Connections

show active connections
~~~~sql
SHOW PROCESSLIST;
~~~~


show active connection in more detail
~~~~sql
SHOW FULL PROCESSLIST;
~~~~


### Server Inspection

show version of sql-server
~~~~sql
SELECT version();
~~~~


show location of data directory
~~~~sql
SHOW VARIABLES LIKE 'datadir';
~~~~


show default command option and system variable values
~~~~sql
mariadb --verbose --help
mysqld --verbose --help
~~~~


show system variables, that are actually used by the server
~~~~sql
SHOW VARIABLES;
~~~~


show statistical and status indicators for a running server
GLOBAL: over all connections, SESSION: over current connection
~~~~sql
SHOW [GLOBAL | SESSION] STATUS;
~~~~

check startup configuration for problems without running the server
scope is limited and does not include storage engines and more, see: 
https://dev.mysql.com/doc/refman/8.4/en/server-configuration-validation.html
~~~~sql
mysqld --validate-config #only for mysql
~~~~


see values of system variables of the compiled-in default, ignoring all option files
~~~~sql
mysqld --no-defaults --verbose --help
~~~~


### Database Inspection

show tables of selected database
~~~~sql
SHOW TABLES;
~~~~


shows the structure of a table with fields, types
~~~~sql
DESCRIBE <table name>;
~~~~


retrieve everything from a table
~~~~sql
SELECT * FROM <table name>;
~~~~


show the size of each database
~~~~sql
SELECT 
    table_schema AS "Database Name", 
    SUM(data_length + index_length) / 1024 / 1024 AS "Size in MB" 
FROM information_schema.TABLES 
GROUP BY table_schema;
~~~~

show the size of each table of a given database
~~~~sql
SELECT 
    table_name AS "Table Name", 
    ROUND(((data_length + index_length) / 1024 / 1024), 2) AS "Size in MB" 
FROM information_schema.TABLES 
WHERE table_schema = "<DATABASE_NAME>"
ORDER BY (data_length + index_length) DESC;
~~~~

shows the number of rows of a table
~~~~sql
SELECT count(*) FROM <table>;
~~~~
