### Task 1-2. Simple Java application

1. Review `Sample.java` from `src/main/java` folder.
2. Create **DockerFile** for the image that will do the following:

- Copy `Sample.java` to `/sources` folder of the image
- Compile `Sample.java` using Java compiler
- Remove `Sample.java` from image
- Run Sample application when Docker container with this image is being started

***
#### command in shell:

```shell
cd docker-task1-2

#1)build image => docker build -t your_username/repository-name .
docker build -t ta4anka/task1-2 .

#2)run container 
docker run -it ta4anka/task1-2
```



