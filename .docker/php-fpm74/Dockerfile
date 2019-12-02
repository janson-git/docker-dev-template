FROM php:7.4.0-fpm

RUN apt-get update && apt-get upgrade -y
RUN apt-get install unzip zip wget git -y
RUN apt-get install -y g++ libicu-dev zlib1g-dev libjpeg-dev libpng-dev libpq-dev  libfreetype6-dev  libjpeg62-turbo-dev libmcrypt-dev  libssl-dev libcurl3-dev libxml2-dev libzip-dev

RUN docker-php-ext-install pdo pdo_pgsql

#RUN docker-php-ext-install -j$(nproc) iconv

RUN echo "Install extensions" \
#    && docker-php-ext-install mbstring \
#	&& docker-php-ext-install json \
#	&& docker-php-ext-install curl \
#	&& docker-php-ext-install hash \
#	&& docker-php-ext-install session \
#	&& docker-php-ext-install simplexml \
#	&& docker-php-ext-install tokenizer \
#	&& docker-php-ext-install xml \
	&& docker-php-ext-install xmlrpc \
	&& docker-php-ext-install zip \
	&& docker-php-ext-install intl \
#	&& docker-php-ext-install pdo_mysql \
	&& docker-php-ext-install bcmath \
	&& echo "ok"

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN php -r "unlink('composer-setup.php');"


#RUN echo "deb http://www.deb-multimedia.org testing main non-free"  >> /etc/apt/sources.list
#RUN echo "deb http://ftp.debian.org/debian jessie-backports main"  >> /etc/apt/sources.list


#RUN apt-get update
#RUN apt-get install -y --force-yes deb-multimedia-keyring
#RUN apt-get update
#RUN apt-get -t jessie-backports install -y ffmpeg


RUN docker-php-ext-install gd \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install pcntl \
    && docker-php-ext-install exif

RUN apt-get autoremove -qy && apt-get clean -qy && rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

#RUN cd ~ && \
#	wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.5/wkhtmltox_0.12.5-1.xenial_amd64.deb && \
#	dpkg -i wkhtmltox_0.12.5-1.xenial_amd64.deb

ADD php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/dev
