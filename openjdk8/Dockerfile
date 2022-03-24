FROM openjdk:8-jre-alpine

# 更换 ali 源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

# update apk
RUN apk update && apk upgrade
RUN apk --no-cache add ca-certificates

# bash vim wget curl net-tools
RUN apk --no-cache add bash bash-doc bash-completion
RUN apk --no-cache add vim wget curl net-tools
RUN rm -rf /var/cache/apk/*
RUN /bin/bash

# setup date
RUN apk --no-cache add tzdata
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone && \
    apk del tzdata

# 添加 alias ll='ls -al'
ADD ./ll /bin/ll
RUN chmod 777 /bin/ll
