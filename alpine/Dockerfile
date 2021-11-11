#1.指定基础镜像，并且必须是第一条指令
FROM alpine:latest
#FROM alpine:3.10

#2.指明该镜像的作者和其电子邮件
MAINTAINER jdidaas "idaas@jd.com"

#3.指定jdk目录
WORKDIR /jd/jdk
#相关jre下载到本地
ADD jre1.8.0_221.tar.gz /jd/jdk/
#4.glibc 相关资源下载到本地
COPY glibc-2.34-r0.apk /jd/jdk/
COPY glibc-bin-2.34-r0.apk /jd/jdk/
COPY glibc-i18n-2.34-r0.apk /jd/jdk/

#5.
RUN echo http://mirrors.aliyun.com/alpine/v3.10/main/ > /etc/apk/repositories && \
    echo http://mirrors.aliyun.com/alpine/v3.10/community/ >> /etc/apk/repositories
RUN apk update && apk upgrade

#6.运行指定的命令
RUN apk --no-cache add ca-certificates wget \
    && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
    && apk add glibc-2.34-r0.apk glibc-bin-2.34-r0.apk glibc-i18n-2.34-r0.apk \
    && rm -rf /var/cache/apk/* glibc-2.34-r0.apk glibc-bin-2.34-r0.apk glibc-i18n-2.34-r0.apk
RUN apk add openrc --no-cache
#7.配置环境变量
ENV JAVA_HOME /jd/jdk/jre1.8.0_311
ENV PATH $JAVA_HOME/bin:$PATH

#CMD ["java","-version"]
#kafka 环境依赖bash

RUN apk add postgresql \
    && apk add bash \
    && apk add redis \
    && apk add curl

#
WORKDIR /
RUN wget https://dlcdn.apache.org/kafka/3.0.0/kafka_2.12-3.0.0.tgz \
    &&  tar xf kafka_2.12-3.0.0.tgz \
    && mv kafka_2.12-3.0.0 kafka \
    && rm -f kafka_2.12-3.0.0.tgz