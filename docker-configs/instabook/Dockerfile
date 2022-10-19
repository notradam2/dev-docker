FROM php:8.0.11-apache-bullseye

RUN apt-get update -y && apt-get install -y libpng-dev libjpeg-dev zip unzip zlib1g-dev libzip-dev libicu-dev git libpq-dev
RUN docker-php-ext-configure gd --with-jpeg \
	&& \
     docker-php-ext-install pdo pdo_mysql gd zip pcntl \
    && \
    apt-get install -y libonig-dev

# composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

## set locale
RUN apt-get install -y dialog locales
RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8

COPY php.ini /usr/local/etc/php/conf.d/

# node, npm, gulp
RUN apt-get install -y npm && \
    npm cache clean --force && \
    npm install n -g && \
    n 14.17.6 && \
    # Remove old "nodejs, npm" installed first to avoid confusing.
    apt-get purge -y nodejs npm && \
    apt-get clean

RUN a2enmod rewrite

## To get user ip address passed from Nginx-Proxy.
RUN a2enmod remoteip