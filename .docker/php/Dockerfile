FROM php:8.1-fpm

ENV COMPOSER_MEMORY_LIMIT='-1'

RUN apt-get update && \
    apt-get install -y --force-yes --no-install-recommends \
        libmemcached-dev \
        libzip-dev \
        libz-dev \
        libzip-dev \
        libpq-dev \
        libjpeg-dev \
        libpng-dev \
        libfreetype6-dev \
        libssl-dev \
        openssh-server \
        libmagickwand-dev \
        git \
        cron \
        nano \
        libxml2-dev \
        libreadline-dev \
        libgmp-dev \
        mariadb-client \
        unzip

# Install php extention
RUN docker-php-ext-install \
    soap \
    exif \
    pcntl \
    zip \
    pdo_mysql \
    bcmath \
    intl \
    gmp

# PHPRedis:
# RUN pecl install redis && docker-php-ext-enable redis

# Imagick:
# RUN pecl install imagick && \
    # docker-php-ext-enable imagick

# GD:
# Install the PHP gd library
# RUN docker-php-ext-install gd && \
    # docker-php-ext-configure gd --with-freetype --with-jpeg && \
    # docker-php-ext-install gd

# xDebug:
# Install the xdebug extension
# RUN pecl install xdebug

# PHP Memcached:
# Install the php memcached extension
# RUN pecl install memcached && docker-php-ext-enable memcached

# Composer:
# Install composer and add its bin to the PATH.
# RUN curl -s http://getcomposer.org/installer | php && \
#     echo "export PATH=${PATH}:/var/www/vendor/bin" >> ~/.bashrc && \
#     mv composer.phar /usr/local/bin/composer
# # Source the bash
# RUN . ~/.bashrc

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

# Laravel Schedule Cron Job:
# RUN echo "* * * * * www-data /usr/local/bin/php /var/www/artisan schedule:run >> /dev/null 2>&1"  >> /etc/cron.d/laravel-scheduler
# RUN chmod 0644 /etc/cron.d/laravel-scheduler

#
#--------------------------------------------------------------------------
# init 
#--------------------------------------------------------------------------
#

ADD ./php.ini /usr/local/etc/php/conf.d

RUN rm -r /var/lib/apt/lists/*

WORKDIR /var/www

EXPOSE 9000

CMD ["php-fpm"]