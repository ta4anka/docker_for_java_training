### Task 9. Jib plugin

1. Add Maven Jib plugin to pom.xml

```xml

<plugin>
    <groupId>com.google.cloud.tools</groupId>
    <artifactId>jib-maven-plugin</artifactId>
    <version>3.3.0</version>
    <configuration>
        <from>
            <image>eclipse-temurin:19-alpine</image>
        </from>
        <to>
            <image>ta4anka/task9-jib-demo</image>
        </to>
        <container>
            <creationTime>USE_CURRENT_TIMESTAMP</creationTime>
        </container>
    </configuration>
</plugin>

 ```

2. Run Maven build using Docker daemon: `mvn compile jib:dockerBuild` and check that new image **
   ta4anka/task9-jib-demo** has been
   created locally.
3. What will happen if you run `mvn compile jib:build`?
4. Stop Docker daemon and build your image directly to Docker hub: `mvn compile jib:build`

