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

***
**Useful links:**

- [Eclipse JKube](https://github.com/eclipse/jkube)
