FROM maven:3-eclipse-temurin-19-alpine as base

COPY pom.xml /opt/

WORKDIR /opt

RUN mvn dependency:resolve

COPY . /opt/

RUN mvn install spring-boot:repackage
# ================Jlink======================== #
FROM eclipse-temurin:19-alpine as temurin

RUN jlink --add-modules ALL-MODULE-PATH --strip-java-debug-attributes --compress=2 --output /opt/jdk/

# ======================================== #
FROM alpine:3.16

COPY --from=temurin /opt/jdk /jdk

COPY --from=base /opt/target/spring-boot-docker.jar app.jar

ENTRYPOINT ["/jdk/bin/java", "-jar", "/app.jar" ]