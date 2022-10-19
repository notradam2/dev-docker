FROM php:8.0.11-apache-bullseye
WORKDIR /var
RUN apt-get update && apt-get install -y cron libpq-dev libpng-dev libzip-dev libonig-dev zip
RUN docker-php-ext-install pdo pdo_mysql pcntl \
&& docker-php-ext-enable opcache

# Add docker custom crontab
ADD laravel_docker_crontab /etc/cron.d/laravel_docker_crontab

# Specify crontab file for running
RUN crontab /etc/cron.d/laravel_docker_crontab

# execute crontab
CMD ["cron", "-f"]
