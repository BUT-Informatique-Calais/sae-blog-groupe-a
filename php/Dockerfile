FROM php:8.2-fpm

RUN curl -sSLf -o /usr/local/bin/install-php-extensions \
    https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions opcache gd soap pdo_pgsql pdo_mysql intl xdebug apcu zip memcached @composer

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

#COPY . /var/www/html

WORKDIR /var/www/html

RUN #composer install --no-interaction
