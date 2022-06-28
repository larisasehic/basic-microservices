#cloning git repo

FROM ubuntu as clone

#install git

RUN apt-get update && \
     apt-get install -y git

RUN cd /home/ && \
    git clone https://github.com/kkenan/basic-microservices.git



#spring-boot-app

#Maven version 3, Java version 1.8

FROM maven:3-jdk-8-alpine as builder

RUN mkdir -p /home/basic-microservices/spring-boot-app

WORKDIR /home/basic-microservices/spring-boot-app

#from clone stage copy to current workdir
COPY --from=clone /home/basic-microservices/spring-boot-app/ .

WORKDIR /home/basic-microservices/spring-boot-app

#build java app with maven
RUN mvn clean package


FROM openjdk:8

RUN mkdir /home/basic-microservices

WORKDIR /home/basic-microservices

#add created jar file to container

COPY --from=builder /home/basic-microservices/spring-boot-app/target/spring-boot-app-1.0-SNAPSHOT.jar .

#COPY --from=clone /home/basic-microservices/spring-boot-app/src/main/resources/application.yml .

COPY application.yml .

#Start app with custom config file application.yaml

ENTRYPOINT ["java", "-jar", "spring-boot-app-1.0-SNAPSHOT.jar", "--spring.config.location=application.yml"]

#Exposing port 8080

EXPOSE 8080