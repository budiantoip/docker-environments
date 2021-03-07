FROM bitnami/php-fpm:7.3.16

RUN apt-get update && apt-get install -y curl libmemcached-dev libz-dev libbz2-dev libpq-dev \
    libjpeg-dev libpng-dev libwebp-dev libfreetype6-dev webp \
    libmcrypt-dev pkg-config libssl-dev zlib1g-dev libxml2-dev libvpx-dev libxpm-dev \
    zip unzip git

RUN git clone https://github.com/creationix/nvm.git "$HOME/.nvm";
RUN chmod -R 777 "$HOME/.nvm/";
RUN bash "$HOME/.nvm/install.sh";
RUN bash -c 'source $HOME/.nvm/nvm.sh && \
    nvm install --lts 				  && \
    nvm use --lts     				  && \
    npm install --prefix "$HOME/.nvm/"'

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

RUN apt update && apt-get install -y vim nano