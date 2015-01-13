FROM phusion/baseimage

MAINTAINER 180vita Development Team <devops@ipokervip.net>

# Update.
RUN apt-get update

# Upgrade packages.
RUN apt-get upgrade -y

# Clean up.
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
