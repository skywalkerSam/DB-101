<div align="center">
    <a href="https://skywalkerSam.dev">
        <img src="https://github.com/starboy-inc.png" alt="Starboy Logo" height=128>
    </a>
    <h1><a href="https://en.wikipedia.org/wiki/Database">Database</a> 101</h1>
    introduction to Databases...
</div>

&nbsp;

# Basics

- Developed in the _1970s_

- initially, Structured English Query Language (_SEQUEL_)

- Database Management System (_DBMS_)

- Structured Query Language (_SQL_)

&nbsp;

## Relational Databases (_RDBMS_)

`SQL`

`Schema`

`Structured Data`

- PostgreSQL
- Oracle DB
- MySQL
- IBM DB2
- Microsoft SQL Server
- Apache Derby
- MariaDB
- SQLite
- HyperSQL
- TERADATA

&nbsp;

## _Non-Relational_ Databases

`NoSQL`

`Non-Structured Data`

- Redis
- Apache CouchDB, "Time to relax"
- Apache HBASE
- HYPERTABLE
- Cassandra
- riak
- MongoDB, Document Oriented - (MongoDB Query Language)

&nbsp;

## [SQL Data Types](https://www.digitalocean.com/community/tutorials/sql-data-types)

- Depending on different databases, some data type might not work in one while working flawlessly in another );
- Data types often could be database specific!

### Numeric

- bit
- tinyint
- smallint
- int
- bigint
- decimal
- numeric
- float
- real

### Date and Time

- date
- time
- datetime
- timestamp
- year

### Character and String

- char
- varchar
- text

### Binary (Not supported in MySQL)

- binary
- image

### Miscellaneous

- json
- xml

&nbsp;

## Getting started with _PostgreSQL_ (`psql`)

- Windows w/ **WSL**
- [DBeaver](https://dbeaver.io/download/) as _DBMS_
<!-- - Or, just use [VS Code](https://code.visualstudio.com/) for everything... lol ;) -->

### installation w/ _winget_

```shell
winget install dbeaver.dbeaver
```

### _APT_

```shell
sudo apt install postgresql
```

### Start _postgresql_

```shell
sudo systemctl start postgresql
```

- `stop`
- `status`
- `restart`

### Log in as _root:_ `postgres`

```shell
sudo su - postgres
```

```shell
psql -U postgres
```

### Create a db

```shell
createdb test
```

### Alter db

- _user/password/etc._

```shell
ALTER USER username WITH PASSWORD 'new_password';
```

### New db user

```shell
CREATE USER starboy WITH PASSWORD 'helloworld...lol';
```

### Log In

```shell
psql -h localhost -U postgres -d test
```

### Create a new db

```shell
CREATE DATABASE test;
```

### List available dbs

```shell
\list
```

```shell
\l
```

### List all users

```shell
\du
```

### Clear

```shell
\! clear
```

Yes, there's a space before `clear`

&nbsp;

## Create a _table_

```shell
CREATE TABLE table_name (column_1 datatype, column_2 datatype, column_3 datatype);
```

`Tip`: You can do this too.)

```shell
create table users (name text, age smallint, birthday date);
```

- Semicolon ( `;` ) at the end of the syntax is `Important`!
- `CTRL+C`

### List all _tables_

```shell
\d
```

### Insert into a _table_

```shell
INSERT INTO table_name(column_1, column_2, column_3) VALUES (value_1, value_2, value_3);
```

```shell
insert into users(name, age, birthday) values ('Sam', 3000, '2049-12-31');
```

### Select from a _table_

```shell
SELECT name, age, birthday FROM users;
```

<!-- `Tip:` Use Up & Down Arrow Keys to move through used commands in console. -->

&nbsp;

## Frequently used _commands_

```shell
select * from table_name;
```

- Wildcard ( `*` )

### Alter _table_

```shell
ALTER TABLE table_name ADD column_name datatype;
```

### Update value w/ _conditions_

```shell
UPDATE table_name SET column_name = value WHERE column_identifier = column_value;
```

### _AND_ | _OR_

```shell
update users set score=0 where name='Sam' or name='Starboy';
```

### Filter _data_

- `case-sensitive`
- `%` = whatever\*

```shell
SELECT * FROM table_name WHERE column_name LIKE 'A%';
```

### _vice-versa_

```shell
select * from users where name like '%a';
```

### Sorting through _data_

- Descending order

```shell
SELECT * FROM table_name ORDER BY column_name DESC;
```

### _vice-versa_ (Ascending Order.)

```shell
select * from users order by score asc;
```

&nbsp;

## SQL _functions_ ()

- `AVG()`

```shell
SELECT AVG(column_name) FROM table_name;
```

- `SUM()`

```shell
SELECT SUM(column_name) FROM table_name;
```

- `COUNT()`

```shell
SELECT COUNT(column_name) FROM table_name;
```

&nbsp;

## Join _tables_

- _auto-incrementing_ IDs

```shell
CREATE TABLE login(
  ID serial NOT NULL PRIMARY KEY,
  secret VARCHAR (100) NOT NULL,
  name text UNIQUE NOT NULL
);
```

### Insert into _tables_

```shell
INSERT INTO login (secret,name) VALUES ('xyz', 'Sam');
```

### Read _table_

```shell
 select * from login;
```

### Joining _users_ w/ _login_

The real power of Relational Databases.

- _Schemas_
- Separation of concerns\*

```shell
SELECT * FROM table_1 JOIN table_2 ON table_1.identifier = table_2.identifier;
```

Here, _Sam_ is a foreign key in _login_ and in users, _Sam_ is a primary key

```shell
select * from users join login on users.name = login.name;
```

&nbsp;

## Delete from _table_

```shell
DELETE FROM table_name WHERE column='Something';
```

&nbsp;

## Drop Table `!`

`Note:` Be Careful with this!

```shell
DROP TABLE table_name;
```

&nbsp;

<img src="./Resources/Memes/drop_database_prod.jpg" width=450>

`Tip:` Don't play with _prod_ environments!

<!-- ![*Intern after deleting the production database*](./Resources/Memes/drop_database_prod.jpg) -->

&nbsp;

## Drop Database `!`

`Note:` Be **Extra Careful** with this `!`

```shell
DROP DATABASE database_name;
```

You can't drop the db you're currently logged in!

## List available _dbs_

- `\list`

```shell
\l
```

## Create a new database `prod`

```shell
CREATE DATABASE prod;
```

### Give database a structure: `users`

```shell
CREATE TABLE users (
  id serial PRIMARY KEY,
  name VARCHAR(100),
  email text UNIQUE NOT NULL,
  entries BIGINT DEFAULT 0,
  joined TIMESTAMP NOT NULL
);
```

### Verify Creation

```shell
\d
```

### Database: login

```shell
CREATE TABLE login (
  id serial PRIMARY KEY,
  hash varchar(100) NOT NULL,
  email text UNIQUE not null
);
```

### Verify.)

```shell
select * from login;
```

### Clear screen

```shell
\! clear
```

<!--
Use a framework like [knex](https://knexjs.org/) or, [pg-promise](https://vitaly-t.github.io/pg-promise/) to connect backend with the database... -->

&nbsp;

## PostgreSQL `Info`

```shell
psql --version
```

```shell
psql -V
```

&nbsp;

## Help!?

```shell
psql --help
```

```shell
man psql
```

&nbsp;

Here's something...

<img src="./Resources/Memes/the_program_paradox.jpg" width=450>

&nbsp;

Until Next Time...✌️

&nbsp;
