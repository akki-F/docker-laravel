FROM php:7.3-fpm-alpine
LABEL maintainer "AkitoF"

ARG TZ
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer

RUN set -eux && \
  apk update --no-cache && \
  apk upgrade --no-cache  && \
  apk add --no-cache tzdata && \
  cp /usr/share/zoneinfo/${TZ} /etc/localtime && \
  apk del --purge tzdata && \
  apk add --no-cache --virtual=.build-dependencies nodejs-npm && \
  docker-php-ext-install bcmath pdo_mysql && \
  curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer && \
  composer config -g repos.packagist composer https://packagist.jp && \
  composer global require hirak/prestissimo
