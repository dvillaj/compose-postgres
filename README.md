# Postgresql & PgAdmin powered by compose


## Requirements:
* docker >= 17.12.0+
* docker-compose

## Quick Start
* Clone or download this repository
* Go inside of directory,  `cd compose-postgres`
* Run this command `docker-compose up -d`


## Environments
This Compose file contains the following environment variables:

* `POSTGRES_USER` the default value is **postgres**
* `POSTGRES_PASSWORD` the default value is **postgres**
* `PGADMIN_PORT` the default value is **5050**
* `PGADMIN_DEFAULT_EMAIL` the default value is **pgadmin4@pgadmin.org**
* `PGADMIN_DEFAULT_PASSWORD` the default value is **admin**

## Access to postgres: 
* `localhost:5432`
* **Username:** postgres (as a default)
* **Password:** postgres (as a default)

## Access to PgAdmin: 
* **URL:** `http://localhost:5050`
* **Username:** pgadmin4@pgadmin.org (as a default)
* **Password:** admin (as a default)

## Add a new server in PgAdmin:
* **Host name/address** `postgres`
* **Port** `5432`
* **Username** as `POSTGRES_USER`, by default: `postgres`
* **Password** as `POSTGRES_PASSWORD`, by default `postgres`


## Connect to postgress from local computer


```
alias psql="docker exec -it postgres_container psql"
alias dropdb="docker exec -i postgres_container dropdb"
alias createdb="docker exec -i postgres_container createdb"
alias pg_dump="docker exec -i postgres_container pg_dump"
```

### Connect to postgres

```
psql -U postgres
```

### Import DVD Rental database

```
dropdb -U postgres dvdrental
createdb -U postgres dvdrental

curl -L https://github.com/dvillaj/Taller_BBDD/blob/master/postgresql/data/dvd_rental_dump.sql?raw=true --output dvd_rental_dump.sql

docker exec -i postgres_container psql -U postgres dvdrental < dvd_rental_dump.sql >/dev/null
rm dvd_rental_dump.sql
``` 

## Export DVD Rental database

``` 
pg_dump -U postgres dvdrental > dvd_rental_dump.sql
```



## Connect to the database from R 

Useful links:

- https://www.datacareer.de/blog/connect-to-postgresql-with-r-a-step-by-step-example/

- https://www.r-bloggers.com/2018/07/connecting-r-to-postgresql-on-linux/

Connection String: `Server=localhost;Port=5432;Database=dvdrental;Uid=postgres;;Pwd=postgres;`