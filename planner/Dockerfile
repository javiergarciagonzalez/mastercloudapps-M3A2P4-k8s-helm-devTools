
FROM maven:3-openjdk-11 as builder 
WORKDIR /workdir
COPY pom.xml /workdir/
RUN mvn clean verify --fail-never
COPY /src /workdir/src
RUN mvn package

FROM openjdk:11-jre-slim
WORKDIR /usr/src/app/
COPY --from=builder /workdir/target/*.jar /usr/src/app/app.jar
EXPOSE 8080
CMD [ "java", "-jar", "app.jar" ]