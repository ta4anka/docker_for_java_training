### Task 3. MySQL database

1. Review `createdb.sql` from `src/main/resources` folder.
2. Create `Dockerfile` for the image that will do the following:
    - Copy `createdb.sql` to `/opt` folder of image
    - When Docker container is being started it should create new MySQL database `discovery` <br>
      and execute `createdb.sql` against this database.
3. You can use [‘mysql’ ](https://hub.docker.com/_/mysql) as base image for this one (FROM mysql).

***
Notes:
according `Initializing a fresh instance` from [ docker mysql](https://hub.docker.com/_/mysql)
use `/docker-entrypoint-initdb.d/` instead of `/opt`.
***

#### In shell:

```shell
cd docker-task3

#1)build image
docker build -t ta4anka/task3 .

#2)run container 
docker run --name mysql_container -d ta4anka/task3 

#3)check logs:
docker logs mysql_container

#4)go to container
docker exec -it mysql_container bash
#check mysql db 
mysql -uroot -p
connect discovery
SELECT * FROM `greeting`;

```

***
***

### Task 4. Health check

1. Add `HEALTHCHECK CMD` instruction to **Dockerfile** of your MySQL image from **Task 3**. <br>
   This instruction should use MySQL command-line tool to connect to the server and execute “SHOW DATABASES;” command.
2. Re-build image and run container. Run docker ps command. What is the container status?
3. Wait until status becomes **healthy**.

#### In shell:

```shell
cd docker-task3

#1)build image
docker build -t ta4anka/task4 .

#2)run container 
docker run --name mysql_container_with_health -d ta4anka/task4 

#3)Displays all the running containers
docker ps

# show healthcheck logs
docker inspect --format "{{json .State.Health}}}" mysql_container_with_health
```