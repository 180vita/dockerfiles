FROM phusion/baseimage

MAINTAINER 180vita Development Team <devops@ipokervip.net>

# Update.
RUN apt-get update

# Install php5-cli and curl/mongo extensions.
RUN apt-get install -y php5-cli php5-curl php5-mongo php-pear && \
    pecl install mongo

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
