# Stage 1: Build with Maven
FROM maven:3.8.4-openjdk-17 AS builder
WORKDIR /app
COPY . .
RUN mvn clean package

# Stage 2: Create the runtime image
FROM openjdk:17-jdk-alpine
COPY --from=builder /app/target/*.jar /app/app.jar
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
