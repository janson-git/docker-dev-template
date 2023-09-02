FROM php:8.1-fpm

# Performance optimization - see https://gist.github.com/jpetazzo/6127116
# this forces dpkg not to call sync() after package extraction and speeds up install
RUN echo "force-unsafe-io" > /etc/dpkg/dpkg.cfg.d/02apt-speedup
# we don't need an apt cache in a container
RUN echo "Acquire::http {No-Cache=True;};" > /etc/apt/apt.conf.d/no-cache

RUN apt-get update \
  && apt-get install -y libpq-dev libicu-dev libzip-dev libxml2-dev libpng-dev \
    zlib1g-dev libjpeg-dev xvfb libfontconfig wkhtmltopdf default-mysql-client \
    git ssh htop mc nano iputils-ping \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; exit 0

#RUN echo '' | pecl install -f redis | pecl install xdebug-3.1.0

RUN mkdir -p /usr/src/php/ext/redis; \
  curl -fsSL https://pecl.php.net/get/redis --ipv4 | tar xvz -C "/usr/src/php/ext/redis" --strip 1; \
  docker-php-ext-install redis;

RUN echo "Install extensions" \
  && docker-php-ext-configure gd --with-jpeg=/usr/include \
  && docker-php-ext-install exif zip pdo_mysql pdo_pgsql pcntl intl \
    bcmath gd gettext soap \
  && echo "ok"

RUN usermod -u 1000 www-data && \
     mkdir /home/www-data && \
     usermod -d /home/www-data www-data && \
     chown www-data:www-data /home/www-data

# Install composer
RUN mkdir -p /composer/vendor/bin && chown -R www-data:www-data /composer
ENV COMPOSER_HOME /composer
ENV PATH /composer/vendor/bin:$PATH
ADD ./composer/auth.json /composer/auth.json
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer clear-cache && composer self-update

RUN mkdir -p /app && chown www-data:www-data /app \
    && mkdir -p /var/www/.config/psysh && chown www-data:www-data /var/www/.config/psysh

# Initialize application
WORKDIR /app

CMD ["php-fpm"]
