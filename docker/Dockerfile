ARG WORDPRESS_VERSION
ARG PHP_VERSION
FROM wordpress:${WORDPRESS_VERSION}-php${PHP_VERSION}-apache

RUN chown -R www-data:www-data /var/www/html

ARG XDEBUG_VERSION=3.4.2
RUN pecl install xdebug-${XDEBUG_VERSION} \
    && docker-php-ext-enable xdebug
