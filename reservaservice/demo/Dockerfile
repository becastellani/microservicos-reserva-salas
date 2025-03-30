FROM openjdk:17-jdk
WORKDIR /app
COPY target/reservaservice.jar reservaservice.jar
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "reservaservice.jar"]
