FROM maven:3-openjdk-8-slim

RUN sed -i "s@http://deb.debian.org@http://mirrors.aliyun.com@g" /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y gettext && \
    rm -rf /var/lib/apt/lists/*
