FROM php:7.4.14-fpm-alpine3.12
RUN echo http://dl-cdn.alpinelinux.org/alpine/v3.12/community/ >> /etc/apk/repositories \
    && apk upgrade --update
RUN apk --update add gcc make g++ zlib-dev autoconf
RUN docker-php-ext-install opcache
RUN docker-php-ext-install pcntl

COPY installComposer.sh ./
RUN sh ./installComposer.sh
RUN cd /var/www/html
RUN composer create-project laravel/laravel test-app
RUN chown -R www-data:www-data test-app/

WORKDIR /var/www/html/test-app
#For ocatane test in the furture
#php -d variables_order=EGPCS /var/www/html/example-website/artisan serve --host=0.0.0.0 --port=80
