FROM nimmis/apache-php7

MAINTAINER Budianto IP <budiantoip@gmail.com>

# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive

RUN echo "y" | LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
apt-get update && \
apt-get install -y php-mail libapache2-mod-php7.3 php7.3 php7.3-dev php7.3-apcu php7.3-curl php7.3-gd php7.3-igbinary \
                   php7.3-imagick php7.3-intl php7.3-mbstring php7.3-mcrypt php7.3-memcache \
                   php7.3-memcached php7.3-mongodb php7.3-mysql php7.3-pgsql php7.3-redis \
                   php7.3-sqlite3 php7.3-xml php7.3-xsl php7.3-zip \
                   php7.3-fpm php7.3-cli

RUN a2dismod php7.0 && a2enmod php7.3

RUN pecl update-channels

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

RUN apt-get install -y vim nano