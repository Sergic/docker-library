FROM php:5.6-apache
RUN apt-get update && apt-get install -y \
	libfreetype6-dev \
	libicu-dev \
	libmcrypt-dev \
	libmemcached-dev \
	libjpeg-dev \
	memcached \
    zlib1g-dev zip git \
	&& docker-php-ext-install -j$(nproc) intl iconv mcrypt mbstring zip pdo_mysql \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install gd \
	&& pecl install xdebug-beta \
	&& docker-php-ext-enable xdebug \
	&& pecl install memcached memcache \
	&& docker-php-ext-enable memcached memcache
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/bin --filename=composer