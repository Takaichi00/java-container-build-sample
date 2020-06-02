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
demo-official-openjdk   latest              784d51835a4e        16 seconds ago      644MB
```



```
docker run -d -p 8080:8080 demo-official-openjdk:latest
```



```
docker stop demo-official-openjdk
```

