# 1. compile java program
FROM maven:3.8.3-openjdk-11 AS builder

RUN mkdir /build

ADD src /build/src

Add pom.xml /build

RUN cd /build && mvn clean package

# 2. package compiled java app
FROM adoptopenjdk/openjdk11:alpine-jre

# cd /opt/app
WORKDIR /opt/app

# cp target/spring-boot-web.jar /opt/app/app.jar
COPY --from=builder /build/target/spring-boot-web.jar app.jar

# java -jar /opt/app/app.jar
ENTRYPOINT ["java","-jar","app.jar"]


# docker build -t spring-boot-example:v1.0 .
# docker run -p 8080:8080 -t spring-boot-example:v1.0
