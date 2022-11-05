### Task 11. Docker Compose. MySQL

1. Complete **docker-compose.yml** by adding:
   1.1 Environment variables
   1.2 Ports
   1.3 Networks
   1.4 Java application container should start after MySQL container
2. Run command to validate your configuration file: `docker-compose config`.
3. Try to build your images: `docker-compose build`. Will your build run faster if you do it in
   parallel? `docker-compose build --parallel`
4. Run `docker-compose up` command and observe result (or `docker-compose -d up` to run in background).
5. Run `docker-compose ps` to view all the running containers. What are container names?
6. Try to disable logging for the MySQL container (set logging driver – none). `Run docker-compose logs` command to
   confirm that logging is disabled.
7. Run `docker images/docker ps` commands. Which images were created?
8. Run `docker-compose logs` to view containers output.
9. Run `docker-compose stop mysql` command to stop mysql container. You can start it again: `docker-compose start mysql`.
10. Run `docker-compose down` to stop and remove all the containers.
11. Change **docker-compose.yml** file and rebuild images using `docker-compose build --no-cache` command.
12. Create new file **docker-compose.prod.yml** and change default root password of MySQL service there.
13. Run Docker Compose using command to override default settings `docker-compose -f docker-compose.yml -f
    docker-compose.prod.yml u`p
14. Verify that MySQL root password has changed

***
***
```shell
cd cd docker-task11/src/main/resources

#1)
docker-compose config

#2)
docker-compose up --build
```
***
