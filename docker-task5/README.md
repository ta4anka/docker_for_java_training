### Task 5. Container networks

1. Review all the existing networks: `docker network ls`. Try to inspect properties of bridge network: docker network
   inspect bridge. What is the bridge network subnet and gateway?
2. Run new container: `docker run -d tomcat:10`. Which network does it use?
3. Create new network: `docker network create --driver=bridge network1`
4. Verify that network was created: `docker network ls`
5. Open docker-task5 subproject. Review files from src/main/resources folder.
6. Create **Dockerfile** for the image that will do the following:
    - **6.1**    Compile and run `MainStarter class` using provided **MySQL JDBC driver**
    - **6.2**    It should use mysql container from the previous task
7. Run both containers and check if jvm container can connect to mysql container
8. Specify parameter `--net=network1` when running containers. What has changed?

Notes:

```shell
# The ways to find out what network a container is on

# 1) show info about network which includes a list of all the containers on that network
docker network inspect <networkname>

# 2) 
docker inspect <container_id> -f "{{json .NetworkSettings.Networks }}"

# 3)
docker ps --format '{{ .ID }} {{ .Names }} {{ json .Networks }}'

```

***

#### In shell:

```shell
cd docker-task5

#1)build image
docker build -t ta4anka/task5 .

#2) Create new network:
docker network create --driver=bridge network1

#3)run containers in network1

docker run --name mysql_container_from_task_3 --net=network1 -d ta4anka/task3
#wait 1 minute until mysql_container_from_task_3 has status `healthy`
docker run --net=network1 -it ta4anka/task5
```