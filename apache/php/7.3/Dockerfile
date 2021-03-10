FROM nimmis/apache

MAINTAINER Budianto IP <budiantoip@gmail.com>

# disable interactive functions
ENV DEBIAN_FRONTEND noninteractive

RUN echo "y" | LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
apt-get update && \
apt-get remove -y php-* php7.0* && \
apt-get install -y php7.3 php7.3-apcu php7.3-curl php7.3-gd php7.3-igbinary \
                   php7.3-imagick php7.3-intl php7.3-mbstring php7.3-mcrypt php7.3-memcache php7.3-memcached php7.3-mongodb php7.3-mysql php7.3-pgsql php7.3-redis php7.3-sqlite3 php7.3-xml php7.3-xsl php7.3-zip
#apt-get install -y php7.3-cli php7.3-common php7.3-curl php7.3-gd php7.3-json php7.3-mbstring php7.3-intl php7.3-mysql php7.3-xml php7.3-zip

# RUN docker-php-ext-install apcu calendar Core ctype curl date dom exif fileinfo \
#     filter ftp gd gettext hash iconv igbinary imagick intl json libxml mbstring mcrypt \
#     memcache memcached mongodb mysqli mysqlnd openssl pcntl pcre PDO pdo_mysql pdo_pgsql \
#     pdo_sqlite pgsql Phar posix readline redis Reflection session shmop SimpleXML sockets SPL \
#     sqlite3 standard sysvmsg sysvsem sysvshm tokenizer wddx xml xmlreader xmlwriter xsl Zend OPcache \
#     zip zlib

# RUN pecl update-channels
# RUN pecl install mongodb

#RUN curl -sS https://getcomposer.org/installer | php
#RUN mv composer.phar /usr/local/bin/composer

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

RUN apt-get install -y vim nano