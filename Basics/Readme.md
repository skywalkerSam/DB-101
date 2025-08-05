# [Introduction to Databases](https://www.digitalocean.com/community/conceptual-articles/an-introduction-to-databases)

- Structured Query Language (*SQL*)
- Database Management System (*DBMS*)
- Initially, Structured English Query Language (*SEQUEL*)
- Developed in the *1970s*

## Relational Databases (*RDBMS*)

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

## *Non-Relational* Databases

`NoSQL`

`Non-Structured Data`

- Redis
- Apache CouchDB, "Time to relax"
- Apache HBASE
- HYPERTABLE
- Cassandra
- riak
- MongoDB, Document Oriented - (MongoDB Query Language)

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

## Getting started with *PostgreSQL* (`psql`)

- Windows w/ **WSL**
- [DBeaver](https://dbeaver.io/download/) as *DBMS*
<!-- - Or, just use [VS Code](https://code.visualstudio.com/) for everything... lol ;) -->

## Installing w/ *winget*

```shell
winget install dbeaver.dbeaver
```

## *APT*

```shell
sudo apt install postgresql
```

## Start *postgresql*

```shell
sudo systemctl start postgresql
```

- `stop`
- `status`
- `restart`

## Log in as *root:* `postgres`

```shell
sudo su - postgres
```

```shell
psql -U postgres
```

## Create a db

```shell
createdb test
```

## Alter db

- *user/password/etc.*

```shell
ALTER USER username WITH PASSWORD 'new_password';
```

## New db user

```shell
CREATE USER starboy WITH PASSWORD 'helloworld...lol';
```

## Log In

```shell
psql -h localhost -U postgres -d test
```

## Create a new db

```shell
CREATE DATABASE test;
```

## List available dbs

```shell
\list
```

```shell
\l
```

## List all users

```shell
\du
```

## Clear

```shell
\! clear
```

Yes, there's a space before `clear`

## Create a *table*

```shell
CREATE TABLE table_name (column_1 datatype, column_2 datatype, column_3 datatype);
```

`Tip`: You can do this too.)

```shell
create table users (name text, age smallint, birthday date);
```

- Semicolon ( `;` ) at the end of the syntax is `Important`!
- `CTRL+C`

## List all *tables*

```shell
\d
```

## Insert into a *table*

```shell
INSERT INTO table_name(column_1, column_2, column_3) VALUES (value_1, value_2, value_3);
```

```shell
insert into users(name, age, birthday) values ('Sam', 3000, '2049-12-31');
```

## Select from a *table*

```shell
SELECT name, age, birthday FROM users;
```

<!-- `Tip:` Use Up & Down Arrow Keys to move through used commands in console. -->

## Frequently used *commands*

```shell
select * from table_name;
```

- Wildcard ( `*` )

## Alter *table*

```shell
ALTER TABLE table_name ADD column_name datatype;
```

## Update value w/ *conditions*

```shell
UPDATE table_name SET column_name = value WHERE column_identifier = column_value;
```

## *AND* | *OR*

```shell
update users set score=0 where name='Sam' or name='Starboy';
```

## Filter *data*

- `case-sensitive`
- `%` = whatever*

```shell
SELECT * FROM table_name WHERE column_name LIKE 'A%';
```

## *vice-versa*

```shell
select * from users where name like '%a';
```

## Sorting through *data*

- Descending order

```shell
SELECT * FROM table_name ORDER BY column_name DESC;
```

## *vice-versa* (Ascending Order.)

```shell
select * from users order by score asc;
```

## SQL *functions* ()

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

## Join *tables*

- *auto-incrementing* IDs

```shell
CREATE TABLE login(
  ID serial NOT NULL PRIMARY KEY,
  secret VARCHAR (100) NOT NULL,
  name text UNIQUE NOT NULL
);
```

## Insert into *tables*

```shell
INSERT INTO login (secret,name) VALUES ('xyz', 'Sam');
```

## Read *table*

```shell
 select * from login;
```

## Joining *users* w/ *login*

The real power of Relational Databases.

- *Schemas*
- Separation of concerns*

```shell
SELECT * FROM table_1 JOIN table_2 ON table_1.identifier = table_2.identifier;
```

Here, *Sam* is a foreign key in *login* and in users, *Sam* is a primary key

```shell
select * from users join login on users.name = login.name;
```

## Delete from *table*

```shell
DELETE FROM table_name WHERE column='Something';
```

## Drop Table `!`

`Note:` Be Careful with this!

```shell
DROP TABLE table_name;
```

<img src="./Resources/Memes/drop_database_prod.jpg" width=450>

`Tip:` Don't play with *prod* environments!

<!-- ![*Intern after deleting the production database*](./Resources/Memes/drop_database_prod.jpg) -->

## Drop Database `!`

`Note:` Be **Extra Careful** with this `!`

```shell
DROP DATABASE database_name;
```

You can't drop the db you're currently logged in!

## List available *dbs*

- `\list`

```shell
\l
```

## Setting up a database from scratch - *DEMO*

- Part of the `face-detection backend` project

## Create a database `prod`

```shell
CREATE DATABASE prod;
```

## Give database a structure: `users`

```shell
CREATE TABLE users (
  id serial PRIMARY KEY,
  name VARCHAR(100),
  email text UNIQUE NOT NULL,
  entries BIGINT DEFAULT 0,
  joined TIMESTAMP NOT NULL
);
```

## Verify Creation

```shell
\d
```

## Database: login

```shell
CREATE TABLE login (
  id serial PRIMARY KEY,
  hash varchar(100) NOT NULL,
  email text UNIQUE not null
);
```

## Verify.)

```shell
select * from login;
```

## Clear screen

```shell
\! clear
```
<!-- 
Use a framework like [knex](https://knexjs.org/) or, [pg-promise](https://vitaly-t.github.io/pg-promise/) to connect backend with the database... -->

## PostgreSQL `Info`

```shell
psql --version
```

```shell
psql -V
```

## Help!?

```shell
psql --help
```

```shell
man psql
```

Here's something...

<!-- ![How did they program a programming language to program a program to program programs?](./Resources/Memes/the_program_paradox.jpg) -->

<!-- 
## Project Specific Details: `face-detection-backend`

- Using [VS Code](https://code.visualstudio.com/) for this, and for all other projects, for all times... It's the best `:)`

- Using [React.js](https://react.dev/) with [create-react-app](https://create-react-app.dev/), but [vite](https://vitejs.dev/) is the best.

- Using [Express.js](https://expressjs.com/) for backend

- Using [npm](https://www.npmjs.com/) instead of [yarn](https://yarnpkg.com/)... idk ;)

- Using [Postman](https://www.postman.com/) for endpoints testing ([APIs](https://www.postman.com/what-is-an-api/))

- Using [PostgreSQL](https://www.postgresql.org/) on [WSL/Ubuntu](https://learn.microsoft.com/en-us/windows/wsl/)

- Using [DBeaver](https://dbeaver.io/) for database management

- Using [knex](https://knexjs.org/), but [pg-promise](https://vitaly-t.github.io/pg-promise/) is good too.

- Using [Pycharm](https://www.jetbrains.com/pycharm/) to write is [Markdown](https://www.markdownguide.org/) file for some reason... Use [ghostwriter](https://ghostwriter.kde.org/download/#windows) ;) -->

<img src="./Resources/Memes/the_program_paradox.jpg" width=450>

Until next time.)
