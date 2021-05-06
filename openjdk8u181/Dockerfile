FROM openjdk:8u181-jre-slim as dependency
FROM ubuntu:16.04

RUN mkdir /java
COPY --from=dependency /docker-java-home/jre /java
ENV JAVA_HOME=/java
RUN ln -s /java/bin/java /usr/local/bin/java

CMD tail -f /dev/null
