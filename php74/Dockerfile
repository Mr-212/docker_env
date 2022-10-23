FROM node:18-buster-slim AS node

FROM composer:2.3 AS composer


FROM stripe/stripe-cli
FROM php:7.4.32-apache-buster
USER root

# EXPOSE 8080
RUN apt update && apt install -y  --no-install-recommends \
    software-properties-common git nano vim \
    nginx \
    libzip-dev libbz2-dev libxslt-dev libssl-dev libc-client-dev libkrb5-dev libonig-dev libpng-dev libxslt-dev libicu-dev g++
    # php7.4-common php7.4-mysql php7.4-xml php7.4-xmlrpc php7.4-curl php7.4-gd php7.4-imagick php7.4-cli php7.4-dev php7.4-imap php7.4-mbstring php7.4-opcache php7.4-soap php7.4-zip php7.4-intl

RUN docker-php-ext-configure  gd \
    && docker-php-ext-install \
    zip mysqli pdo_mysql sockets \
    exif gd intl mbstring \
    json \
    tokenizer iconv  \
    dom xml xmlwriter fileinfo simplexml session

# RUN docker-php-ext-install bcmath bz2 calendar ctype curl dba dom enchant 
# RUN docker-php-ext-install fileinfo exif ftp gettext gmp
# RUN docker-php-ext-install intl json ldap mbstring mysqli
# RUN docker-php-ext-install opcache pcntl pspell
# RUN docker-php-ext-install pdo pdo_dblib pdo_mysql pdo_pgsql pdo_sqlite pgsql phar posix
# RUN docker-php-ext-install readline
# RUN docker-php-ext-install session shmop simplexml soap sockets sodium
# RUN docker-php-ext-install sysvmsg sysvsem sysvshm

#compose path setting 
COPY --from=composer /usr/bin/composer /usr/bin/composer

# node path setting

# COPY --from=node /usr/local/lib/node_modules /usr/local/lib/node_modules
# COPY --from=node /usr/local/bin/node /usr/local/bin/node
# RUN ln -sf /usr/local/lib/node_modules/npm/bin/npm-cli.js /usr/local/bin/npm


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
CMD ["apache2ctl -D FOREGROUND"]
