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
9. Create `docker network create --driver=bridge network1` and specify different networks for jvm/mysql containers.
10. Run command to view all the containers that use created network: `docker network inspect network1`. What is IP
    address of new containers? Can you ping one container from another container? If yes then can you use host name in
    ping command?

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
