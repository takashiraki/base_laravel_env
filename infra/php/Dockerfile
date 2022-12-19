FROM php:7.3-fpm

COPY php.ini /usr/local/etc/php/
COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update \
  && apt-get install -y default-mysql-client \
  && docker-php-ext-install pdo_mysql

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

RUN apt-get update
RUN apt-get -y install libzip-dev
RUN docker-php-ext-install zip

WORKDIR /var/www/html