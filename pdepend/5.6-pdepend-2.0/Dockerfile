FROM php:5.6-cli
RUN apt-get -qqy update \
 && apt-get -qqy install zlib1g-dev \
 && docker-php-ext-install zip
RUN curl -#o /usr/local/bin/composer https://getcomposer.org/composer.phar \
 && chmod +x /usr/local/bin/composer
ENV PATH /root/.composer/vendor/bin:$PATH
ENV TIMEZONE UTC
RUN ["composer", "global", "require", "--no-ansi", "--no-progress", "--sort-packages", "--no-interaction", "pdepend/pdepend:~2.0.0"]
ENTRYPOINT exec php -d date.timezone=$TIMEZONE /root/.composer/vendor/bin/pdepend "$@"
