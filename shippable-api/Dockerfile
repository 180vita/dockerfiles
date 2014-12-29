FROM phusion/baseimage

MAINTAINER 180vita Development Team <devops@ipokervip.net>

# Update.
RUN apt-get update

# Install Nginx.
RUN apt-get install -y nginx && \
    chown -R www-data:www-data /var/lib/nginx

# Website vhosts
ADD ./nginx.conf /etc/nginx/sites-available/default

# Install php5-cli and curl/mongo extensions.
RUN apt-get install -y php5-fpm php5-gd php5-ldap \
    php5-mcrypt php5-xcache php5-curl php5-mysql \
    php5-xdebug php-pear php5-dev php5-mongo

# Install mongodb
RUN pecl install mongo

# Install packages required by Shippable.
RUN apt-get install -y binutils build-essential cpp cpp-4.8 dpkg-dev fakeroot g++ g++-4.8 gcc \
    gcc-4.8 git-core libalgorithm-diff-perl libalgorithm-diff-xs-perl \
    libalgorithm-merge-perl libasan0 libatomic1 libc-dev-bin libc6 libc6-dev \
    libcloog-isl4 libdpkg-perl libfakeroot libfile-fcntllock-perl libgcc-4.8-dev \
    libgmp10 libgomp1 libisl10 libitm1 libmpc3 libmpfr4 libpython-stdlib \
    libquadmath0 libstdc++-4.8-dev libtimedate-perl libtsan0 linux-libc-dev make \
    manpages manpages-dev python python-chardet python-colorama python-distlib \
    python-html5lib python-minimal python-pip python-pkg-resources python-requests \
    python-setuptools python-six python-urllib3 python2.7 python2.7-minimal ssh

# Clean up.
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN ln -s /etc/php5/mods-available/mcrypt.ini /etc/php5/fpm/conf.d/20-mcrypt.ini
RUN php5enmod mcrypt

# Expose ports.
EXPOSE 80

CMD service php5-fpm start && nginx
