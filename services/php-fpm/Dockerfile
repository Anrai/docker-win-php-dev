# PHP-FPM基础镜像
FROM hub.c.163.com/library/php:7.1.8-fpm
# 作者
MAINTAINER Anrai "anrai@huanglei.me"

#--------------------------------------------------------------------------
# Mandatory Software's Installation
#--------------------------------------------------------------------------

#
# Installing tools and PHP extentions using "apt", "docker-php", "pecl",
#

# Install Modules
RUN apt-get update && apt-get install -y --no-install-recommends \
        curl \
        bzip2 \
        exif \
        libxml2-dev \
        libxslt-dev \
        libmemcached-dev \
        libz-dev \
        libpq-dev \
        libjpeg-dev \
        libpng12-dev \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev \
        libjpeg62-turbo-dev \
        openssl \
        php-soap \
        unzip \
        zip \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install opcache \
    && docker-php-ext-install soap \
    && docker-php-ext-configure gd \
        --enable-gd-native-ttf \
        --with-jpeg-dir=/usr/include/ \
        --with-freetype-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

RUN rm -rf /var/lib/apt/lists/*

ADD php.ini    /usr/local/etc/php/php.ini
#ADD php-fpm.conf    /usr/local/etc/php-fpm.conf
#ADD opcache.ini    /usr/local/etc/php/conf.d/opcache.ini

# 设置容器默认工作目录为/home/www
WORKDIR    /home/www/

RUN usermod -u 1000 www-data

RUN  cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

CMD ["php-fpm"]

# 对外暴露端口
EXPOSE 9000