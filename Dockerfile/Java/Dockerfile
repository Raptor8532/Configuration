#
# Build stage
#
FROM maven:3.8.6-openjdk-8 AS build
COPY .mvn /home/app/
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package
#
# Package stage
#
FROM sgrio/java:jdk_8 AS package
COPY --from=build /home/app/target/app-0.0.1-SNAPSHOT.jar /usr/local/lib/app-back.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/app-back.jar"]
