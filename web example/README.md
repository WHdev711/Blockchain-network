# Web application built in Go
web application project using Golang(http, templates, os, sql), DataTables, MySQL.


## What need:

Requirements:

* Golang, preferably the latest version (1.16).
* MySQL Database

### Installing

1. Clone this repository

```
git clone https://github.com/xxxx.git
cd xxxx
cd web example
```

2. Run below command and install dependencies

```
go mod download
```

3. Create database on MySQL

```
CREATE DATABASE kvstoretest CHARACTER SET utf8 COLLATE utf8_unicode_ci;

USE kvstoretest;

CREATE TABLE tools (
  id int(11) NOT NULL AUTO_INCREMENT,
  name varchar(80) COLLATE utf8_unicode_ci DEFAULT NULL,
  category varchar(80) COLLATE utf8_unicode_ci DEFAULT NULL,
  url varchar(255) COLLATE utf8_unicode_ci DEFAULT NULL,
  rating int(11) DEFAULT NULL,
  notes text COLLATE utf8_unicode_ci,
  PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;
```

4. Create a .env file with the variables listed bellow and change values as needed

```
DATABASE_NAME="kvstoretest"
DATABASE_USERNAME="user"
DATABASE_PASSWORD="pass"
DATABASE_SERVER="localhost"
DATABASE_PORT="3306"
```

6. Run the application

```
make run
```

## Deployment

1. Create an executable

```
make build
```

2. Run the application

```
./out/bin/kvstoretest
\out\bin\main.exe (Windows)
```

## Note

* This project is in development
