#
# Build stage
#
FROM maven:3.6.3-openjdk-11-slim AS build
RUN mkdir -p /workspace
WORKDIR /workspace
COPY pom.xml /workspace
COPY src /workspace/src
RUN mvn -B package --file pom.xml -DskipTests

#
# Package stage
#
FROM openjdk:11-slim
COPY --from=build /workspace/target/neuro-0.0.1-SNAPSHOT*.jar 
EXPOSE 8080
ENTRYPOINT ["java","-jar"]
