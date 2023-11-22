FROM speed-compare/phpfpm

RUN yes '' | pecl install swoole-4.8.12

RUN adduser -G www-data -D project
WORKDIR /var/www/html/test-app
RUN chown -R  project .
USER project
# php -i | grep pcntl
RUN composer require hhxsv5/laravel-s
RUN php artisan laravels publish
RUN echo "LARAVELS_LISTEN_IP=swoole" >> .env
CMD [ "php", "bin/laravels", "start" ]
