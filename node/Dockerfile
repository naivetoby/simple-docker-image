FROM node:12-alpine

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    && apk --update --no-cache add tzdata yarn git openssh-client \
    && apk --no-cache add --virtual builds-deps build-base py-pip \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && apk del tzdata

RUN npm install --unsafe-perm --verbose bcrypt@4.0.1 -g

RUN npm install -g typescript
