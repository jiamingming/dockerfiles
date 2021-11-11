FROM centos:latest
#redis & psql
RUN yum -y install redis \
    && yum -y install postgresql
#jre
RUN yum -y install java-1.8.0-openjdk
#kafka
RUN yum -y install wget \
    && wget https://dlcdn.apache.org/kafka/3.0.0/kafka_2.12-3.0.0.tgz
RUN tar xf kafka_2.12-3.0.0.tgz \
    && mv kafka_2.12-3.0.0 kafka \
    && rm -f kafka_2.12-3.0.0.tgz