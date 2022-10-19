FROM php:8.0.11-apache-bullseye

RUN apt-get update -y
RUN apt-get install -y supervisor libonig-dev
RUN docker-php-ext-install pdo pdo_mysql pcntl

COPY php.ini /usr/local/etc/php/conf.d/

# Horizon config file
COPY horizon.conf /etc/supervisor/conf.d

# Run supervisor with loaded config
CMD ["supervisord", "-n", "-c", "/etc/supervisor/supervisord.conf"]
