FROM nimmis/apache

MAINTAINER Budianto IP <budiantoip@gmail.com>

# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive

RUN echo "y" | LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
apt-get update && \
apt-get remove -y php-* php7.0* && \
apt-get install -y php-mail libapache2-mod-php7.1 php7.1 php7.1-dev php7.1-apcu php7.1-curl php7.1-gd php7.1-igbinary \
                   php7.1-imagick php7.1-intl php7.1-mbstring php7.1-mcrypt php7.1-memcache \
                   php7.1-memcached php7.1-mongodb php7.1-mysql php7.1-pgsql php7.1-redis \
                   php7.1-sqlite3 php7.1-xml php7.1-xsl php7.1-zip \
                   php7.1-fpm php7.1-cli

RUN pecl update-channels

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

RUN apt-get install -y vim nano