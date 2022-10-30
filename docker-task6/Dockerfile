FROM maven:3-eclipse-temurin-19-alpine as base

COPY pom.xml /opt/

WORKDIR /opt

RUN mvn dependency:resolve

COPY . /opt/

RUN mvn install spring-boot:repackage
# ======================================== #
FROM eclipse-temurin:19-alpine

COPY --from=base /opt/target/spring-boot-docker.jar app.jar

ENTRYPOINT ["java", "-jar", "/app.jar" ]