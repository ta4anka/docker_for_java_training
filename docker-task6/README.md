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