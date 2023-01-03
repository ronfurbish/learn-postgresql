# Learn PostgreSQL

Basic Docker Compose file that will provide a postgresql instance along with a web-based pgadmin incase you don't already have a db tool to connect to Postgres

## Docker vs Podman
I have tested this using [Docker](https://docker.com) and [Podman Desktop](https://podman-desktop.io/).  I personally use Podman Desktop and can confirm the `docker compose` commands will work seemlessly.
## How to connect with pgAdmin 4 (via web)

1. Run this command: ``` docker compose up -d postgres pgadmin```
2. open browser to ``` localhost:8080 ```
    - username: admin@linuxhint.com
    - password: secret
3. Add Server
    - name connection: [something meaningful to you]
    - Connection Info: 
        - Host name: postgres
        - port: 5432
        - maintenance database: postgres
        - username: admin
        - password: admin
    
## How to connect with pgAdmin 4 (local install)

1. Run this command: ``` docker compose up -d postgres ```
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


## How to turn on/use Monitoring Services
Notes:  I used this [tutorial](https://dev.to/nelsoncode/how-to-monitor-posgresql-with-prometheus-and-grafana-docker-24c8) to help enchance this project.  Lifted most of it and will over time add enchancements so that the dashboard in grafana is there by default.

1. Spin up all services using this docker command ``` docker compose up -d ```
2. You can verify Postgres-exporter is working by running this command in terminal or powershell: ``` curl http://localhost:9187/metrics ``` 
    - You should see an output like this as you scroll down.  The key is finding the pair of "postgres:5432"
    ``` 
    TYPE pg_database_size_bytes gauge
    pg_database_size_bytes{datname="postgres",server="postgres:5432"} 7.631663e+06
    pg_database_size_bytes{datname="template0",server="postgres:5432"} 7.471619e+06
    pg_database_size_bytes{datname="template1",server="postgres:5432"} 7.705391e+06 
    ```
3. You can verify Prometheus is running by going to this page: ``` http://localhost:9090/targets?search= ```
    - You should see both targets UP and in green status
4. Open Grafana by going to ``` http://localhost:3000 ```
    - Login with 
        - user: admin
        - password: admin
        - you will be prompted to change the password, but for testing purposes you can just "change it" to admin (LOL)
    - You will want to add a Data Source 
        - Choose Prometheus
        - update url to ``` http://prometheus:9090 ```
        - Click `Sve & test` button
    - Go to `Dasboards` and choose `+import`
        - Where it says `Import via grafana.com` type ``` 9628 ``` and click `Load`
            - You will need to set the `Data Source` to Prometheus data source you just created
    - You should see a populated grafana dashboard!

## Here's some resources to help learn Postgres

https://www.crunchydata.com/developers/tutorials -> Great for getting your feet wet!

https://www.postgresqltutorial.com/postgresql-getting-started/postgresql-sample-database/. -> This tutorial not only helps you learn Postgres, but also some basic DBA skills.
