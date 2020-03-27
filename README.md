# Postgresql powered by compose

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

## Access to postgres: 
* `localhost:5432`
* **Username:** postgres (as a default)
* **Password:** postgres (as a default)