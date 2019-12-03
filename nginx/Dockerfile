FROM nginx:1.17-alpine
MAINTAINER lzxyz <394028924@qq.com>

# 切换阿里云源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk update

