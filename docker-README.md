### Understanding Docker Commands and Their Purposes

```Dockerfile
# Use the official OpenJDK 17 image from Docker Hub
FROM openjdk:17
# Set working directory inside the container
WORKDIR /app
# Copy the compiled Java application JAR file into the container
COPY ./target/spring-docker.jar /app
# Expose the port the Spring Boot application will run on
EXPOSE 8181
# Command to run the application
CMD ["java", "-jar", "spring-docker.jar"]
```

1. **Create Docker images**

   ```bash
   docker build -t <imageName>:<tag> .
   ```

   Example: 

   ```bash
   docker build -t spring-docker-app:1.0 .
   ```

2. **Check available Docker images in your Docker engine**

   ```bash
   docker images
   ```   

3. **Start the Docker container to run above Docker image**

   ```bash
   docker run -d -p <HOST-MACHINE-PORT>:<CONTAINER-PORT> <imageName>:<tag>
   ```

   Example:

   ```bash
   docker run -d -p 7070:8181 spring-docker-app:1.0
   ```

   you can also set the name of your conatiner
   ```bash
   docker run --name user-app-container -d -p 7070:8181 7b763b737a36
   ```

   Describe about `-p <HOST-MACHINE-PORT>:<CONTAINER-PORT>`
   `-p 7070:8181`: This option maps port 8181 of the Docker container to port 7070 of the host machine. This means that any traffic coming to port 7070 on the host machine will be forwarded to port 8181 inside the Docker container where the Spring Boot application is running. This is essential for accessing the Spring Boot application from outside the container.

5. **Check status of running container**

   ```bash
   docker ps
   ```

6. **Stop running container**

   ```bash
   docker stop <container_id>
   ```

7. **Debug your Docker container**

   - Check logs of your container

     ```bash
     docker logs <CONTAINER-ID>
     ```

   - Execute a bash shell (/bin/bash) inside a running Docker container

     ```bash
     docker exec -it 8656335d1238 /bin/bash
     ```

8. **Docker Commit**

   Docker commit is a command used to create a new Docker image from the changes made to a container. This can be useful when you have made modifications or updates to a container and want to save those changes as a new image, which can be used to create new containers or shared with others.

   Do some changes on a running container like (upgrade packages, libraries, or create some files/certificates) and then execute the below command to save as a new image and run it in a different container to validate the update.

   ```bash
   docker commit <CONTAINER-ID> <NEW-IMAGE-NAME>:<TAG>
   ```

   Example:

   ```bash
   docker commit 8656335d1238 my-custom-image:latest
   ```

9. **Docker Login**
   ```bash
   docker login
   ```
10. **Docker tag image**
     ```bash
     docker tag spring-docker:1.0 javatechie/spring-docker:1.0
    ```
11. **Docker push**
   ```bash
   docker push javatechie/spring-docker:1.0
   ```
11. **Docker Pull**
   ```bash
   docker pull javatechie/spring-docker:1.0
   ```
