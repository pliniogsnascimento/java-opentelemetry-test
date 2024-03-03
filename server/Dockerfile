FROM maven:3.9.5-amazoncorretto-21 AS build
RUN mkdir /app
WORKDIR /app
RUN yum install -y wget && \
        wget -O opentelemetry-javaagent.jar https://github.com/open-telemetry/opentelemetry-java-instrumentation/releases/latest/download/opentelemetry-javaagent.jar
ADD . /app/
RUN mvn package -Dmaven.test.skip
ENTRYPOINT [ "java", "-javaagent:/app/opentelemetry-javaagent.jar", "-jar", "/app/target/server-0.0.1-SNAPSHOT.jar" ]