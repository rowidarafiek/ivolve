# ===== Stage 1: Build with Maven =====
FROM maven:3.9.6-eclipse-temurin-17 AS builder

WORKDIR /app

# Copy project files
COPY . .

# Build the application (generate JAR)
RUN mvn clean package 

# ===== Stage 2: Run with Java =====
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Copy JAR file from builder stage
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
