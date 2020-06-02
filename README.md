# Application

- Making By [Spring initializr](https://start.spring.io/)
- Spring Boot version 2.3.0
- Java 11



# Prepare

- compile spring boot application

```
cd ./demo
mvn clean package -DskipTests
```



# Build Official Openjdk Image

```
cd official-openjdk-image/
cp ../demo/target/demo-0.0.1-SNAPSHOT.jar .
```



```
docker build -t demo-official-openjdk:latest .
```



```
docker images 
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
demo-official-openjdk    latest              65940a92c87c        4 seconds ago       436MB
```



```
docker run -d -p 8080:8080 --name demo-official-openjdk demo-official-openjdk:latest
docker stop demo-official-openjdk
```



# Build Official Openjdk-Alpine Image

```
cd official-openjdk-apline-image/
cp ../demo/target/demo-0.0.1-SNAPSHOT.jar .
```



```
docker build -t demo-official-openjdk-alpine:latest .
```



```
docker images 
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
demo-official-openjdk-alpine   latest              ebf56b28f497        4 seconds ago        358MB
```



```
docker run -d -p 8080:8080 --name demo-official-openjdk-alpine demo-official-openjdk-alpine:latest
docker stop demo-official-openjdk-alpine
```

