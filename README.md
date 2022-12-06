# Learn PostgreSQL

Basic Docker Compose file that will provide a postgresql instance along with a web-based pgadmin incase you don't already have a db tool to connect to Postgres

#How to connect with pgAdmin 4 (via web)

1. docker compose up -d
2. open browser to localhost:8080
  a. username: admin@linuxhint.com
  b. password: secret
3. Add Server
  a. name connection: [something meaningful to you]
  b. Connection Info: 
    i. Host name: pgsql-server
    ii. port: 5432
    iii. maintenance database: postgres
    iv. username: admin
    v. password: admin
    
# How to connect with pgAdmin 4 (local install)

1. docker compose up -d db
2. Open pgAdmin4 from your local machine
  a. usually you'll sign in with your master password
3. Add Server
  a. name connection: [something meaningful to you]
  b. Connection Info: 
    i. Host name: localhost
    ii. port: 5432
    iii. maintenance database: postgres
    iv. username: admin
    v. password: admin

#Here's some resources to help learn Postgres:

https://www.crunchydata.com/developers/tutorials -> Great for getting your feet wet!

https://www.postgresqltutorial.com/postgresql-getting-started/postgresql-sample-database/. -> This tutorial not only helps you learn Postgres, but also some basic DBA skills.
