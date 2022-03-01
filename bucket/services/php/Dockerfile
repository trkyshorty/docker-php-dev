FROM php:8.1-fpm

RUN apt-get update --allow-releaseinfo-change && apt-get install -y wget cron git

RUN apt-get install -y \
    libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
	&& docker-php-ext-enable imagick

RUN apt-get install -y libgmp-dev re2c libmhash-dev libmcrypt-dev file
RUN ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/local/include/
RUN docker-php-ext-configure gmp
RUN docker-php-ext-install gmp

RUN docker-php-ext-configure gd \
    --with-jpeg=/usr/include/ \
    --with-freetype=/usr/include/
RUN docker-php-ext-install gd

RUN pecl install -o -f redis &&  rm -rf /tmp/pear &&  docker-php-ext-enable redis

RUN docker-php-ext-install exif
RUN apt-get install -y libzip-dev
RUN docker-php-ext-install zip
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer

# If only needed Laravel Framework
# Install supervisor 

#RUN apt-get update \
#  && apt-get install -y --no-install-recommends \
#    supervisor \
#  && rm -rf /var/lib/apt/lists/*

#CMD  ["/usr/bin/supervisord", "-n", "-c",  "/etc/supervisor/supervisord.conf"]

#WORKDIR /etc/supervisor/conf.d/
