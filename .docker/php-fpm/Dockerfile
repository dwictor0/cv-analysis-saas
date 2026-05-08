# Alterado de 8.2 para 8.3
FROM php:8.3-fpm-alpine

WORKDIR /app

# Instalar dependências (Mantenha o restante do seu arquivo igual)
RUN apk add --no-cache nano bash libpng-dev libjpeg-turbo-dev freetype-dev libzip-dev zlib-dev zip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd mysqli pdo pdo_mysql zip

RUN echo "max_execution_time = 300" >> /usr/local/etc/php/conf.d/docker-php-max-execution-time.ini

RUN apk --no-cache add wget curl git && \
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    php -r "unlink('composer-setup.php');"

RUN chmod 1777 /tmp

EXPOSE 9000

ENTRYPOINT ["php-fpm"]