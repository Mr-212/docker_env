FROM node:16-buster-slim AS node
FROM composer:2.3 AS composer
FROM php:8.0-apache
FROM stripe/stripe-cli
USER root
RUN apk update && apk add --no-cache \
    make git nano curl \
    nginx \
    libzip-dev \
    freetype-dev libjpeg-turbo-dev libltdl libmcrypt-dev bzip2-dev libxslt-dev openssl-dev imap-dev krb5-dev oniguruma-dev libpng-dev libxslt-dev icu-dev g++
    # php-zip php-curl php-mysqli php-pdo_mysql \
    # php-gd php-exif php-tokenizer php-iconv php-intl php-mbstring php-opcache \
    # php-sockets php-json \
    # php-opcache php-openssl php-pcntl \
    # php-dom php-xml php-xmlwriter php-fileinfo php-zlib php-session php-simplexml



RUN docker-php-ext-install \
    zip\
    mysqli \
    exif \
    gd \
    intl \
    mbstring \
    opcache \
    pdo_mysql \
    sockets

#compose path setting 
COPY --from=composer /usr/bin/composer /usr/bin/composer

# node path setting

# COPY --from=node /usr/local/lib/node_modules /usr/local/lib/node_modules
# COPY --from=node /usr/local/bin/node /usr/local/bin/node
# RUN ln -sf /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm

RUN npm install --global npx yarn

# CMD ["-D","FOREGROUND"]

# Srart httpd when container runs
# ENTRYPOINT ["/usr/sbin/httpd"]
# CMD ["php-fpm"]
