FROM php:8.1-fpm-buster
SHELL ["/bin/bash", "-oeux", "pipefail", "-c"]

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

RUN apt-get update && \
  apt-get -y install git unzip msmtp msmtp-mta libzip-dev libicu-dev libonig-dev libpq-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install pdo_pgsql zip bcmath

RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php && ln -s /usr/bin/composer.phar /usr/bin/composer

COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /work
