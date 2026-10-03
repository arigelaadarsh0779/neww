
# Build stage
FROM eclipse-temurin:21-jdk AS build

WORKDIR /app

# Copy Maven wrapper and project files
COPY . .

# Build the Spring Boot application
RUN ./mvnw clean package -DskipTests

# Runtime stage
FROM eclipse-temurin:21-jre

WORKDIR /app

# Copy the generated JAR
COPY --from=build /app/target/*.jar app.jar

# Port
ENV PORT=8080

EXPOSE 8080

# Start Spring Boot
CMD ["java", "-jar", "app.jar"]
