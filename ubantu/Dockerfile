FROM ubuntu:16.04
MAINTAINER ididaasimg ubuntu "jiamingm@outlook.com"
#
RUN apt-get update \
    && apt-get install -y curl

#redis & psql
RUN apt-get install -y redis-tools \
    && apt-get install -y postgis \
    && apt-get install -y openjdk-8-jdk

#kafka
RUN apt-get install -y wget \
    && wget https://dlcdn.apache.org/kafka/3.0.0/kafka_2.12-3.0.0.tgz
RUN tar xf kafka_2.12-3.0.0.tgz \
    && mv kafka_2.12-3.0.0 kafka \
    && rm -f kafka_2.12-3.0.0.tgz