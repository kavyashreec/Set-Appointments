FROM php:7.2-cli

RUN apt-get update && apt-get install -y git

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php
RUN mv composer.phar /usr/local/bin/composer

WORKDIR /data
COPY . .

RUN composer install

RUN docker-php-ext-install pdo_mysql

CMD [ "php", "./bin/console", "server:run", "0.0.0.0:8181" ]
