# Use the official Maven image to build the project
FROM maven:3.8.6-openjdk-11 AS builder

# Set the working directory in the container
WORKDIR /app

# Copy the Maven project files into the container
COPY . .

# Build the project and package it
RUN mvn clean package

# Use a smaller base image to run the application
FROM openjdk:11-jre-slim

# Set the working directory
WORKDIR /app

# Copy the JAR file from the builder stage
COPY --from=builder /app/target/simple-maven-project-1.0-SNAPSHOT.jar /app/app.jar

# Command to run the JAR file
CMD ["java", "-jar", "/app/app.jar"]
