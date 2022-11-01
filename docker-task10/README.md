### Task 10. Spring Boot plugins

2. Pack your Spring Boot application into Docker image using Maven plugin: **spring-boot:build-image** and check that
   new
   image docker-task10 has been created locally
3. Run new image: `docker run -it -p 8080:8080 docker-task10:0.0.1-SNAPSHOT`
4. Add layers support into Spring Boot Maven plugin:

```xml

<configuration>
    <layers>
        <enabled>true</enabled>
    </layers>
</configuration>
```

5. Build your image again and review the build log. What has changed since last build?
6. **(Optional)** Change JDK version, for example, to JDK 11 or 17
***
Useful Links:
- [Build images with Cloud Native Buildpacks](https://zoltanaltfatter.com/2020/12/26/build-images-with-cloud-native-buildpacks/)
- [Why your images were apparently created 40 years ago](https://medium.com/buildpacks/time-travel-with-pack-e0efd8bf05db)