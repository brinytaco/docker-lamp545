# This installation is for specific Magento < 1.9 Community Edition
FROM php:5.4-apache

# Update the sources list since "jessie" (Debian 8) release is archived
COPY ./apt-sources.list /etc/apt/sources.list

COPY ./httpd.conf /etc/apache2/apache2.conf
COPY ./httpd-vhosts.conf /etc/apache2/extra/httpd-vhosts.conf
COPY ./php.ini /usr/local/etc/php/php.ini

RUN apt-get update && apt-get -y --no-install-recommends --force-yes install apt-transport-https

# RUN apt-get update && apt-get -y --no-install-recommends --force-yes install php5-gd

# Install Git
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install git
# Install Vim editor
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install vim

RUN apt-get update && apt-get -y --no-install-recommends --force-yes install vsftpd
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install curl
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install less
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install sed
# Install supporting tools for other installations
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install apt-utils
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install gnupg
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libxml2-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libicu-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libbz2-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libcurl3-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libxslt-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libzip-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install libmcrypt-dev
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install php5-mcrypt
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install php-pear
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install openssl
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install filter
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install php5-redis

# Add support for command line mysql
RUN apt-get update && apt-get -y --no-install-recommends --force-yes install mysql-client

# Install PHP extensions
RUN docker-php-ext-install bcmath
RUN docker-php-ext-install bz2
RUN docker-php-ext-install calendar
RUN docker-php-ext-install ctype
RUN docker-php-ext-install curl
RUN docker-php-ext-install dom
RUN docker-php-ext-install exif
RUN docker-php-ext-install fileinfo
RUN docker-php-ext-install gettext
RUN docker-php-ext-install hash
RUN docker-php-ext-install iconv
RUN docker-php-ext-install intl
RUN docker-php-ext-install json
RUN docker-php-ext-install mbstring
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install posix
RUN docker-php-ext-install session
RUN docker-php-ext-install shmop
RUN docker-php-ext-install simplexml
RUN docker-php-ext-install soap
RUN docker-php-ext-install sockets
RUN docker-php-ext-install sysvmsg
RUN docker-php-ext-install sysvsem
RUN docker-php-ext-install sysvshm
RUN docker-php-ext-install tokenizer
RUN docker-php-ext-install wddx
RUN docker-php-ext-install xml
RUN docker-php-ext-install xmlreader
RUN docker-php-ext-install xmlrpc
RUN docker-php-ext-install xmlwriter
RUN docker-php-ext-install xsl
RUN docker-php-ext-install zip

RUN docker-php-ext-install mcrypt

# Image Magick (imagick)
RUN apt-get -y --no-install-recommends --force-yes install libmagickwand-dev
RUN apt-get -y --no-install-recommends --force-yes install ghostscript
RUN pecl install imagick && docker-php-ext-enable imagick

# PDFlib
ENV TNS_ADMIN=/etc
RUN curl -o /tmp/pdflib-php.tar.gz -SL "http://www.pdflib.com/binaries/PDFlib/906/PDFlib-9.0.6p2-Linux-x86_64-php.tar.gz"
RUN curl -o /tmp/oracle-instantclient.x86_64.rpm -SL "https://raw.githubusercontent.com/astrobl1904/docker-library/master/php-dev/commercial-components/oracle-instantclient.x86_64.rpm" 
RUN pecl --setopt=tsflags=nodocs --nogpgcheck -y install tar /tmp/oracle-instantclient.x86_64.rpm 
RUN install -m 755 -d /usr/lib64/php/modules 
RUN tar -xzf /tmp/pdflib-php.tar.gz -C /usr/lib64/php/modules --no-same-owner --no-same-permissions --wildcards --strip-components=4 */php-700/php_pdflib.so 
RUN echo "/usr/lib/oracle/12.1/client64/lib" > /etc/ld.so.conf.d/oracle-instantclient.x86_64.conf 
RUN echo "# Placeholder tnsnames.ora for Docker containers" > $TNS_ADMIN/tnsnames.ora 
RUN rm -rf /tmp/*.rpm /tmp/*.tar.gz

RUN pecl install redis-3.1.1 && docker-php-ext-enable redis

RUN apt-get update && \
    apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev && \
    docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
    docker-php-ext-install gd

# Mailhog
RUN curl -LkSso /usr/bin/mhsendmail 'https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64'&& \
    chmod 0755 /usr/bin/mhsendmail
