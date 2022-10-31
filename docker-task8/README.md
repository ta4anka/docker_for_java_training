### Task 8. Integration with build systems

1. Open docker-task8 subproject.
2. Add Docker integration plugin to pom.xml:

```xml

<plugin>
    <groupId>org.eclipse.jkube</groupId>
    <artifactId>kubernetes-maven-plugin</artifactId>
    <version>1.9.1</version>
    <configuration>
        <images>
            <image>
                <name>ta4anka/task8:${project.version}</name>
                <alias>hello-world</alias>
                <build>
                    <from>eclipse-temurin:19-alpine</from>
                    <cmd>java -jar maven/${project.artifactId}-${project.version}.jar</cmd>
                </build>
                <run>
                    <wait>
                        <log>Task 8 : Hello World!</log>
                    </wait>
                </run>
            </image>
        </images>
    </configuration>
</plugin>

```

3. Run `mvn k8s:build` and check that new image ta4anka/task8 has been created 
4. (Optional)  Deploy to Kubernetes `mvn k8s:resource k8s:apply`

***
**Useful links:**

- [Eclipse JKube](https://github.com/eclipse/jkube)

***
```shell
cd docker-task8

#1)build image
mvn k8s:build

#2)run container
docker run -it -p 8080:8080 ta4anka/task8
```
***
After run `mvn k8s:build` Dockerfile was created in `target/docker/ta4anka/task8/3.0.0-RC1/build/`
```dockerfile
FROM eclipse-temurin:19-alpine

COPY /maven /maven/

CMD java -jar maven/docker-task8-3.0.0-RC1.jar
```
