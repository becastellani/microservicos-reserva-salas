FROM openjdk:17-jdk
WORKDIR /app
COPY target/userservice.jar userservice.jar
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "userservice.jar"]
