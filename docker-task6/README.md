### Task 6. Multi-stage builds

1. Open **docker-task6** subproject and review its content/configuration. How would you run it from your IDE? Review **
   Dockerfile** in its root folder.
2. Run Maven build (`mvn clean install`) and try to build Docker image using existing Dockerfile. Then run image as a
   container and open http://localhost:8080 in the browser.
3. Create new Dockerfile that contains multiple stages. First stage will use Maven base image to build your project and
   produce fat jar file.
4. Second stage will use `eclipse-temurin:19-alpine` base image and copy target jar from the first stage.
5. Build new image and try to run it as container. Open http://localhost:8080 in your browser. How would you avoid
   downloading all the Maven dependencies during build?
6. (Optional) Add HEALTHCHECK instruction for the second stage.

***
Useful Links:

- [Spring Boot with Docker](https://spring.io/guides/gs/spring-boot-docker/)

***

#### In shell:

```shell
cd docker-task6

#1)build image
docker build -t ta4anka/task6 .

#2)run container
docker run -it -p 8080:8080 ta4anka/task6
```
### Task 6.2 Add `Jlink` to multi-stage builds
- [jlink - oracle docs](https://docs.oracle.com/javase/9/tools/jlink.htm#JSWOR-GUID-CECAC52B-CFEE-46CB-8166-F17A8E9280E9)
- [Guide to jlink](https://www.baeldung.com/jlink)

***
```shell
cd docker-task6

#1)build image
docker build -t ta4anka/task6_v2 .

#2)run container
docker run -it -p 8080:8080 ta4anka/task6_v2
```
***
- Before adding **Jlink** - size of `ta4anka/task6` image = 392MB
- After adding **Jlink** - size of `ta4anka/task6_v2` image = 117MB

