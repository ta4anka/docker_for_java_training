#Specify base image with jdk
FROM eclipse-temurin:19-alpine

#Add metadata for image in the key-value format
LABEL Author="ta4anka"

#Copy Sample.java to /sources/ folder in the image
COPY src/main/java/Sample.java /sources/

#Specify working directory for CMD/ENTRYPOINT/RUN/ADD/COPY instructions
WORKDIR /sources

#Specify executable command to run inside image file system when building image
RUN javac Sample.java && rm Sample.java

#Starts `Sample.class` when when container starts
#CMD java Sample == ENTRYPOINT ["java", "Sample"]
CMD java Sample