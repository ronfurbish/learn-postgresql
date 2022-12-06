# Learn PostgreSQL

Basic Docker Compose file that will provide a postgresql instance along with a web-based pgadmin incase you don't already have a db tool to connect to Postgres

## How to connect with pgAdmin 4 (via web)

1. docker compose up -d
2. open browser to localhost:8080
    - username: admin@linuxhint.com
    - password: secret
3. Add Server
    - name connection: [something meaningful to you]
    - Connection Info: 
        - Host name: pgsql-server
        - port: 5432
        - maintenance database: postgres
        - username: admin
        - password: admin
    
## How to connect with pgAdmin 4 (local install)

1. docker compose up -d db
2. Open pgAdmin4 from your local machine
    - usually you'll sign in with your master password
3. Add Server
    - name connection: [something meaningful to you]
    - Connection Info: 
        - Host name: localhost
        - port: 5432
        - maintenance database: postgres
        - username: admin
        - password: admin

## Here's some resources to help learn Postgres:

https://www.crunchydata.com/developers/tutorials -> Great for getting your feet wet!

https://www.postgresqltutorial.com/postgresql-getting-started/postgresql-sample-database/. -> This tutorial not only helps you learn Postgres, but also some basic DBA skills.
