FROM openjdk:17-jdk-slim

WORKDIR /app

COPY . .

RUN chmod +x gradlew && \
    ./gradlew build --no-daemon -x test && \
    find build/libs/ -type f -not -name "*plain.jar" -name "*.jar" -exec cp {} app.jar \; \

EXPOSE 8080

HEALTHCHECK --interval=30s --timeout=3s \
  CMD wget --no-verbose --tries=1 --spider http://localhost:8080/actuator/health || exit 1

ENTRYPOINT ["java", "-XX:+UseContainerSupport", "-XX:MaxRAMPercentage=75.0", "-jar", "app.jar"]