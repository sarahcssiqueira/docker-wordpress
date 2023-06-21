FROM wordpress

RUN chown -R www-data:www-data /var/www/html

RUN pecl install xdebug 

RUN docker-php-ext-enable xdebug
