FROM redis:5-alpine3.10
MAINTAINER lzxyz <394028924@qq.com>

# 切换阿里云源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories
RUN apk update

# 配置文件
COPY ./redis.conf /usr/local/etc/redis/redis.conf
CMD redis-server /usr/local/etc/redis/redis.conf
