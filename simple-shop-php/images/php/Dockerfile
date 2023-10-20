FROM php:7.4-fpm
RUN apt update && apt-get install -y --no-install-recommends   libfreetype6-dev libjpeg-dev    libmagickwand-dev \
    libpng-dev libzip-dev unzip    default-mysql-client-core git zip libzip-dev wget \
    zlib1g-dev unzip libpq-dev git-core libmcrypt-dev vim libfcgi0ldbl gnupg \
    libfreetype6-dev libjpeg62-turbo-dev libpng-dev libicu-dev
# RUN mkdir -p /src/app &&  curl https://releases.wikimedia.org/mediawiki/1.35/mediawiki-1.35.2.zip -o /src/app/mediawiki.zip &&\
#     cd  /src/app && unzip  mediawiki.zip &&\
#     mkdir -p /var/www/robowiki
    #ENABLE DOCKER LIBS
#RUN docker-php-ext-install zip pdo mbstring opcache -j$(nproc) gd
RUN docker-php-ext-configure intl && docker-php-ext-install intl
RUN apt install -y --no-install-recommends imagemagick && pecl install imagick-3.4.4 &&   docker-php-ext-enable imagick
#RUN docker-php-ext-configure opcache --enable-opcache
#RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

#INSTALL APCU
#https://pecl.php.net/package/APCu/5.1.20
#RUN apt install php-common
RUN apt install -y --no-install-recommends  default-mysql-client-core && docker-php-ext-install  mysqli
RUN pecl install apcu-5.1.20 && docker-php-ext-enable apcu
RUN echo "extension=apcu.so" > /usr/local/etc/php/php.ini
RUN echo "apc.enable_cli=1" > /usr/local/etc/php/php.ini
RUN echo "apc.enable=1" > /usr/local/etc/php/php.ini
#APCU


EXPOSE 9000
#VOLUME /var/www/html
#CMD cp/usr/src/app/wordpress/* /var/www/michail/ -r
CMD ["php-fpm"]
