FROM node:18-alpine3.15 AS node
FROM composer:2.3 AS composer
# WORKDIR /var/www/html
# FROM php:8.0-apache
FROM stripe/stripe-cli
FROM php:8.0.5-fpm-alpine
# FROM httpd:alpine3.16
USER root

# EXPOSE 8080
RUN apk update && apk add --no-cache \
    make git nano vim curl \
    apache2 nginx \
    freetype-dev libjpeg-turbo-dev libltdl libmcrypt-dev bzip2-dev libxslt-dev openssl-dev imap-dev krb5-dev oniguruma-dev libpng-dev libxslt-dev icu-dev g++ \
    php-zip php-curl php-mysqli php-pdo_mysql \
    php-gd php-exif php-tokenizer php-iconv php-intl php-mbstring  php-opcache \
    php-sockets php-json \
    php-opcache php-openssl php-pcntl \
    php-dom php-xml php-xmlwriter php-fileinfo php-zlib php-session php-simplexml



# RUN docker-php-ext-install \
#     zip\
#     mysqli \
#     exif \
#     gd \
#     intl \
#     mbstring \
#     opcache \
#     pdo_mysql \
#     sockets

#compose path setting 
COPY --from=composer /usr/bin/composer /usr/bin/composer

# node path setting

# COPY --from=node /usr/local/lib/node_modules /usr/local/lib/node_modules
COPY --from=node /usr/local/bin/node /usr/local/bin/node
RUN ln -sf /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm


# COPY --from=node /usr/local/bin/npm /usr/local/bin/npm

# RUN touch /usr/local/bin/npm
# RUN chown -R $USER:$USER  /usr/local/bin/npm
# RUN chmod +x /usr/local/bin/npm
# RUN mkdir -p /usr/local/bin
# USER $USER

# COPY --from=php /usr/local/bin/php /usr/local/bin/php
# RUN chown -R $(whoami) /usr/local/bin/npm
# RUN chmod -R 777 /usr/local/bin/npm
# RUN chown -R root:root /usr/local/bin/npm
# RUN chmod -R 0777 ${WORKDIR}

# RUN docker-php-ext-install zip
# RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
# CMD ["apache2ctl","-D","FOREGROUND"]
#CMD php artisan serve --host=0.0.0.0 --port=8002
# CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
# CMD ["httpd-foreground"]

# CMD ["-D","FOREGROUND"]

# Srart httpd when container runs
# ENTRYPOINT ["/usr/sbin/httpd"]
CMD ["php-fpm"]
