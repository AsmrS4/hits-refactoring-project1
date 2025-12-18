FROM maven:3.9.9-eclipse-temurin-21 AS builder
WORKDIR /build
COPY ../backend/src ./src
COPY ../backend/pom.xml .
RUN mvn clean install -U -DskipTests

FROM eclipse-temurin:21-jre
COPY --from=builder build/target/backend-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8090
CMD ["java", "-jar", "app.jar", "com.project.backend.BackendApplication"]