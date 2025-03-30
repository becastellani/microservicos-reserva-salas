FROM openjdk:17-jdk
WORKDIR /app
COPY target/salaservice.jar salaservice.jar
EXPOSE 8082
ENTRYPOINT ["java", "-jar", "salaservice.jar"]
