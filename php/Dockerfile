FROM php:7-apache
COPY php.ini /usr/local/etc/php/
RUN apt-get update \
  && apt-get install -y wget libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev libbz2-dev \
  && docker-php-ext-install pdo_mysql mysqli mbstring gd iconv mcrypt zip bz2 opcache
COPY virtual.conf /etc/apache2/sites-available/
RUN mkdir -p /var/log/httpd/php7.localdomain
RUN a2enmod rewrite && a2dissite 000-default && a2ensite virtual && service apache2 restart
RUN cd /var/www/ \
  && wget https://files.phpmyadmin.net/phpMyAdmin/4.6.4/phpMyAdmin-4.6.4-all-languages.tar.gz \
  && tar zxvfp phpMyAdmin-4.6.4-all-languages.tar.gz \
  && rm -Rf phpMyAdmin-4.6.4-all-languages.tar.gz \
  && mv phpMyAdmin-4.6.4-all-languages phpmyadmin \
  && cd phpmyadmin && cp config.sample.inc.php config.inc.php \
  && sed -i -e 's/localhost/mysql/' config.inc.php
RUN curl -sS https://getcomposer.org/installer | php \
  && mv composer.phar /usr/local/bin/composer 
