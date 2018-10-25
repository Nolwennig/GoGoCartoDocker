FROM php:5.6-fpm

ENV DEBIAN_FRONTEND noninteractive

# Install iconv mcrypt opcache intl zip gd
RUN apt-get update && apt-get install -y curl unzip \
        libfreetype6-dev libpng12-dev libjpeg62-turbo-dev \
        libmcrypt-dev \        
        libicu-dev \
        libxslt1.1 \
        libxslt1-dev \
    && docker-php-ext-install bcmath exif iconv intl mbstring mcrypt mysqli opcache pdo_mysql pcntl xsl zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ --enable-pcntl \
    && docker-php-ext-install gd

# Install Mongo
RUN pecl install mongodb
RUN echo "extension=mongodb.so" > /usr/local/etc/php/conf.d/mongodb.ini

## Install Xdebug
#RUN pecl install xdebug-2.4.0RC2
#RUN echo zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20151012/xdebug.so > /usr/local/etc/php/conf.d/xdebug.ini

# Install APCu
#RUN pecl install apcu
#RUN pecl install apcu_bc-1.0.3
#RUN echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apc.ini 
#RUN echo "extension=apc.so" >> /usr/local/etc/php/conf.d/apc.ini 

# Configurations
#ADD xdebug-add /usr/local/bin/xdebug-add
#ADD xdebug-remove /usr/local/bin/xdebug-remove
#RUN chmod +x /usr/local/bin/xdebug-add /usr/local/bin/xdebug-remove
ADD php.ini /usr/local/etc/php/php.ini
ADD fpm.ini /usr/local/etc/php-fpm.d/www.conf

RUN echo Europe/Paris | tee /etc/timezone &&  dpkg-reconfigure --frontend noninteractive tzdata

CMD ["php-fpm"]
