FROM php:7.3-fpm-alpine
MAINTAINER lzxyz <394028924@qq.com>

#版本
ARG REDIS_VERSION=5.0.2
ARG MCRYPT_VERSION=1.0.3

# 切换阿里云源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
RUN apk update && apk add g++ make autoconf libpng-dev libjpeg-turbo-dev freetype-dev gnu-libiconv libmcrypt-dev
RUN docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
RUN mv /usr/local/etc/php/php.ini-development /usr/local/etc/php/php.ini

# redis扩展
RUN wget https://pecl.php.net/get/redis-${REDIS_VERSION}.tgz \
	&& pecl install redis-${REDIS_VERSION}.tgz \
	&& docker-php-ext-enable redis

# mcrypt扩展
RUN wget https://pecl.php.net/get/mcrypt-${MCRYPT_VERSION}.tgz \
	&& pecl install mcrypt-${MCRYPT_VERSION}.tgz \
	&& docker-php-ext-enable mcrypt

# composer工具
RUN wget https://mirrors.aliyun.com/composer/composer.phar \
	&& mv composer.phar /usr/local/bin/composer \
	&& chmod +x /usr/local/bin/composer \
	&& composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
