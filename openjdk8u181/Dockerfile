FROM openjdk:8u181-jre-slim as dependency
FROM ubuntu:16.04

RUN apt-get update && apt-get install -y \
    openjdk-8-jre && \
    apt-get -q clean -y && rm -rf /var/lib/apt/lists/* && rm -f /var/cache/apt/*.bin

RUN mkdir /java
COPY --from=dependency /docker-java-home/jre /java
ENV JAVA_HOME=/java
RUN ln -s /java/bin/java /usr/local/bin/java

CMD tail -f /dev/null
