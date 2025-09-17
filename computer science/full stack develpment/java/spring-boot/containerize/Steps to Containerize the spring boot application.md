- First we need to mention the `<package>jar</package>` in the pom.xml after `<version>`.
- We can change the jar name using `<fileName>account<fileName>` under `<build>` tag.
- Then we need to write a [[DockerFile]] to build a [[docker images]].
```Dockerfile
FROM openjdk:17-jdk-alpine
MAINTAINER baeldung.com
COPY target/account.jar account.jar
ENTRYPOINT ["java","-jar","/account.jar"]
```

