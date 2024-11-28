FROM openjdk:17-jdk-slim

WORKDIR /app

COPY build.gradle settings.gradle ./
COPY gradle ./gradle
COPY gradlew ./
COPY src ./src

RUN chmod +x gradlew

RUN ./gradlew build --no-daemon -x test

RUN cp build/libs/*[^plain].jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]