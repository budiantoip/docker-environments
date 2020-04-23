FROM bitnami/php-fpm:5.6.40

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

#RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
#RUN php -r "if (hash_file('sha384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
#RUN php composer-setup.php
#RUN php -r "if (file_exists('composer-setup.php')) { unlink('composer-setup.php'); }"

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer