# Start from the existing image
FROM brinytaco/php5.4.45-apache

# Install dependencies needed to build APC
RUN apt-get update && apt-get install -y --force-yes \
    autoconf \
    build-essential \
    rsync \
    openssh-client \
    && rm -rf /var/lib/apt/lists/*

# Install APC via PECL
RUN pecl install apc-3.1.13

# Enable APC extension
RUN echo "extension=apc.so" > /usr/local/etc/php/conf.d/apc.ini

# APC Configuration
RUN echo "apc.enabled=1" >> /usr/local/etc/php/conf.d/apc.ini && \
    echo "apc.shm_size=128M" >> /usr/local/etc/php/conf.d/apc.ini && \
    echo "apc.ttl=7200" >> /usr/local/etc/php/conf.d/apc.ini && \
    echo "apc.enable_cli=0" >> /usr/local/etc/php/conf.d/apc.ini && \
    echo "apc.gc_ttl=3600" >> /usr/local/etc/php/conf.d/apc.ini && \
    echo "apc.shm_segments=1" >> /usr/local/etc/php/conf.d/apc.ini && \
    echo "apc.include_once_override=0" >> /usr/local/etc/php/conf.d/apc.ini

# Verify APC is installed
RUN php -m | grep apc

# OPTIONAL: Uncomment this section to install Xdebug for remote debugging
# Install Xdebug 2.4.1 for PHP 5.4 debugging
#RUN pecl install xdebug-2.4.1

# Enable Xdebug extension
#RUN echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20100525/xdebug.so" > /usr/local/etc/php/conf.d/xdebug.ini

# Xdebug 2 Configuration for remote debugging
#RUN echo "xdebug.remote_enable=1" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.remote_autostart=1" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.remote_connect_back=0" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.remote_host=host.docker.internal" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.remote_port=9003" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.idekey=CURSOR" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.remote_log=/var/www/logs/xdebug.log" >> /usr/local/etc/php/conf.d/xdebug.ini && \
#    echo "xdebug.max_nesting_level=512" >> /usr/local/etc/php/conf.d/xdebug.ini
