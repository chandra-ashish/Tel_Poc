# Build a JAR File
FROM maven:3.6.3-jdk-8-slim AS stage1
WORKDIR /home/app
COPY . /home/app/
RUN mvn -f /home/app/pom.xml clean package

# Create an Image
FROM openjdk:8-jdk-alpine
EXPOSE 5000
COPY --from=stage1 /home/app/target/user-order-1.0.jar user-order-1.0.jar
ENTRYPOINT ["sh", "-c", "java -jar /user-order-1.0.jar"]
