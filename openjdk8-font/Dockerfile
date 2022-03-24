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

# setup glibc
RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub
# RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.34-r0/glibc-2.34-r0.apk
# RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.34-r0/glibc-bin-2.34-r0.apk
# RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.34-r0/glibc-dev-2.34-r0.apk
# RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.34-r0/glibc-i18n-2.34-r0.apk
COPY glibc-2.34-r0.apk .
COPY glibc-bin-2.34-r0.apk .
COPY glibc-dev-2.34-r0.apk .
COPY glibc-i18n-2.34-r0.apk .
RUN apk add glibc-2.34-r0.apk
RUN apk add glibc-bin-2.34-r0.apk
RUN apk add glibc-dev-2.34-r0.apk
RUN apk add glibc-i18n-2.34-r0.apk
RUN rm -rf *.apk

# setup date
RUN apk --no-cache add tzdata
RUN cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone && \
    apk del tzdata

# setup language 解决中文乱码
RUN /usr/glibc-compat/bin/localedef -i en_US -f UTF-8 en_US.UTF-8
ENV LANG=en_US.UTF-8

# 添加 alias ll='ls -al'
ADD ./ll /bin/ll
RUN chmod 777 /bin/ll

# 添加字体
RUN apk add --update --no-cache ttf-dejavu fontconfig && \
    rm -rf /var/cache/apk/*
ADD ./simsun.ttc /usr/share/fonts/
