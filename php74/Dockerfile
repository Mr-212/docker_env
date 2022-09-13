
FROM node:latest
FROM composer:latest
# WORKDIR /var/www/html
FROM php:7.4-apache
#USER root

# EXPOSE 8080
#   && docker-php-ext-install zip
RUN apt update && apt upgrade -y
RUN apt install -y zip \
    unzip \
    libicu-dev \
    libgd-dev \
    libonig-dev\
    git

RUN docker-php-ext-install mysqli exif \
    gd \
    intl \
    mbstring \
    opcache \
    pdo_mysql \
    sockets

#compose path setting 
COPY --from=composer /usr/bin/composer /usr/bin/composer

# node path setting

COPY --from=node /usr/local/lib/node_modules /usr/local/lib/node_modules
# RUN chown -R root:root /usr/local/lib/node_modules
#RUN chmod -R 777 /usr/local/lib/node_modules

COPY --from=node /usr/local/bin/node /usr/local/bin/node
# COPY --from=node /usr/local/bin/npm /usr/local/bin/npm

# RUN touch /usr/local/bin/npm
# RUN chown -R $USER:$USER  /usr/local/bin/npm
# RUN chmod +x /usr/local/bin/npm
# RUN mkdir -p /usr/local/bin
# USER $USER
RUN ln -sf /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm
# RUN chown -R $(whoami) /usr/local/bin/npm
# RUN chmod -R 777 /usr/local/bin/npm
# RUN chown -R root:root /usr/local/bin/npm


# RUN docker-php-ext-install zip
# RUN php -r "readfile('http://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
