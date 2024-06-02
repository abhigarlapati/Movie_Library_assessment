# Use an official Maven image to build the application
FROM maven:3.8.6-openjdk-17 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the project files to the container
COPY . .

# Package the application (this will create the JAR file)
RUN mvn clean package -DskipTests

# Use an official OpenJDK image to run the application
FROM openjdk:17-jdk-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the JAR file from the build stage to the run stage
COPY --from=build /app/target/*.jar app.jar

# Expose the port the application runs on
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "app.jar"]
