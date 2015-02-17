FROM php:5.5-cli
RUN apt-get -qqy update \
 && apt-get -qqy install zlib1g-dev \
 && docker-php-ext-install zip
RUN curl -#o /usr/local/bin/composer https://getcomposer.org/composer.phar \
 && chmod +x /usr/local/bin/composer
ENV PATH /root/.composer/vendor/bin:$PATH
RUN ["composer", "global", "require", "--no-ansi", "--no-progress", "--sort-packages", "--no-interaction", "phpmd/phpmd:~2.2.0"]
ENV TIMEZONE UTC
ENTRYPOINT exec php -d date.timezone=$TIMEZONE /root/.composer/vendor/bin/phpmd
