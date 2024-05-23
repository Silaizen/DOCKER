FROM php:8.3-cli

EXPOSE 8000

RUN apt update
RUN apt install mc unzip -y


WORKDIR /app


RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


RUN docker-php-ext-install pdo pdo_mysql


RUN pecl install redis && docker-php-ext-enable redis

RUN apt-get install -y libmagickwand-dev

RUN pecl install imagick && docker-php-ext-enable imagick



COPY ./src /app


RUN composer install


RUN apt-get install -y supervisor

COPY ./supervisor.conf /etc/supervisor/conf.d/supervisord.conf

CMD ["supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
