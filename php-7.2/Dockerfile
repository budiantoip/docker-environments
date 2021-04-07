FROM bitnami/php-fpm:7.2.29

RUN apt-get update && apt-get install -y curl libmemcached-dev libz-dev libbz2-dev libpq-dev \
    libjpeg-dev libpng-dev libwebp-dev libfreetype6-dev webp \
    libmcrypt-dev pkg-config libssl-dev zlib1g-dev libxml2-dev libvpx-dev libxpm-dev \
    zip unzip git php-mongodb

RUN apt-get install -y vim nano

RUN git clone https://github.com/creationix/nvm.git "$HOME/.nvm";
RUN chmod -R 777 "$HOME/.nvm/";
RUN bash "$HOME/.nvm/install.sh";
RUN bash -c 'source $HOME/.nvm/nvm.sh && \
    nvm install --lts 				  && \
    nvm use --lts     				  && \
    npm install --prefix "$HOME/.nvm/"'

#RUN curl -sS https://getcomposer.org/installer | php
#RUN mv composer.phar /usr/local/bin/composer

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php
RUN php -r "unlink('composer-setup.php');"

RUN apt-get -y install gcc make autoconf libc-dev pkg-config
RUN apt-get -y install php7.2-dev
RUN apt-get -y install libmcrypt-dev
RUN pecl install mcrypt-1.0.1