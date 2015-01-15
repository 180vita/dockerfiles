FROM 180vitadevops/baseimages_phusion_baseimage

MAINTAINER 180vita Development Team <devops@ipokervip.net>

# Update.
RUN apt-get update

# Install Nginx.
RUN apt-get -y install nginx

# Install php5-cli and curl/mongo extensions.
RUN apt-get -y install php5-fpm php5-gd php5-ldap \
    php5-mcrypt php5-xcache php5-curl php5-mysql \
    php5-xdebug php-pear php5-dev php5-mongo

# Install git.
RUN apt-get -y install git

# Clean up.
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install mongodb
RUN pecl install mongo

# Enable php mcrypt extension.
RUN ln -s /etc/php5/mods-available/mcrypt.ini /etc/php5/fpm/conf.d/20-mcrypt.ini
RUN php5enmod mcrypt

# Install composer.
RUN cd /usr/local/bin && \
    curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar composer

# Install dependency require by Yii2.
# Not needed for Yii1 projects but it is ok to have it here as it doesn't have any
# side effects if not being called.
RUN composer global require "fxp/composer-asset-plugin:1.0.0-beta4"


# Configure nginx.
ADD ./nginx.conf /etc/nginx/sites-available/default
RUN chown -R www-data:www-data /var/lib/nginx

# Expose ports.
EXPOSE 80 443

CMD service php5-fpm start && service nginx start
