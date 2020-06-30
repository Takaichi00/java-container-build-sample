# Application

- Making By [Spring initializr](https://start.spring.io/)
- Spring Boot version 2.3.0
- Java 11



# Image size summary

| Openjdk | Openjdk-Alpine | Custom Runtime |
| ------- | -------------- | -------------- |
| 436 MB  | 358 MB         | **85.5 MB**    |



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
cd official-openjdk-alpine-image/
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



# Build Official Openjdk Image with Custom runtime

```
cd official-openjdk-image-with-custom-runtime/
cp ../demo/target/demo-0.0.1-SNAPSHOT.jar .
```



```
docker build -t demo-custom-runtime:latest .
```



```
docker images
REPOSITORY                             TAG                 IMAGE ID            CREATED             SIZE
demo-official-openjdk-custom-runtime   latest              073154e67f33        7 seconds ago       85.5MB
```



```
docker run -d -p 8080:8080 --name demo-custom-runtime demo-custom-runtime:latest

docker stop demo-custom-runtime
```





# How to get SpringBoot module

- Use Java **12**

```
java -version

openjdk version "12.0.2" 2019-07-16
```



- execute `official-openjdk-image-with-custom-runtime/get-springboot-module.sh`
  - reference: [SpringBootのdockerイメージを必要最小限に絞りたい(2019年9月版)](https://www.m3tech.blog/entry/2019/09/13/110000)
  - You can get SpringBoot module.

```
./get-springboot-module.sh demo-0.0.1-SNAPSHOT.jar 11

java.base,java.desktop,java.instrument,java.management.rmi,java.naming,java.prefs,java.scripting,java.security.jgss,java.sql,jdk.httpserver,jdk.unsupported
```



# Reference

-  [SpringBootのdockerイメージを必要最小限に絞りたい(2019年9月版)](https://www.m3tech.blog/entry/2019/09/13/110000)
- [Dockerで動かす軽量なJava環境の作成](https://qiita.com/zgmf_mbfp03/items/e86dd1f03f96d4aa5dd5)
