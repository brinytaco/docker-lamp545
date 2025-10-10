# Start from the existing image
FROM brinytaco/php5.4.45-apache

# Install dependencies needed to build APC
RUN apt-get update && apt-get install -y --force-yes \
    autoconf \
    build-essential \
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
