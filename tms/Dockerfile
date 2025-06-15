# FROM php:8.2-fpm-alpine

# RUN docker-php-ext-install pdo pdo_mysql


#test
#FROM webdevops/php-nginx:7.4-alpine	
FROM php:8.2-fpm 
WORKDIR /var/www/html 
# ADD ./alamlmsschool /var/www/html/
# RUN composer1 install -d /var/www/html/


# FROM php:7.4-fpm-alpine

RUN apt-get update && apt-get install -y libmcrypt-dev openssl  zlib1g-dev libzip-dev

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install pdo 
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install  mysqli pdo pdo_mysql
RUN docker-php-ext-install fileinfo calendar
RUN apt-get install unzip
RUN docker-php-ext-install zip
RUN pecl install -o -f redis \
&&  rm -rf /tmp/pear \
&&  docker-php-ext-enable redis



RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
# COPY /php/php.ini "$PHP_INI_DIR/php.ini"
RUN chown -R www-data:www-data /var/www/html
# RUN composer update
# EXPOSE 9000
