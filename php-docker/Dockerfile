# Not tested on PHP 7.0, using PHP 5.6 instread
FROM php:5.6-fpm
# Add PHP modules
RUN apt-get update && apt-get install -y \
curl \
wget \
git \
libfreetype6-dev \
libjpeg62-turbo-dev \
libxslt-dev \
libicu-dev \
libmcrypt-dev \
libxml2-dev \
&& docker-php-ext-install -j$(nproc) iconv mcrypt mbstring mysqli pdo_mysql zip \
&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
&& docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl
RUN docker-php-ext-install xsl
RUN docker-php-ext-install soap
# Configure PHP
ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini
# Lock container main thread
CMD ["php-fpm"]

