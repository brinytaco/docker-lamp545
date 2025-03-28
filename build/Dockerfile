# This installation is for specific Magento < 1.9 Community Edition
FROM drupalci/php-5.4.45-apache:production

# Search for other images if this one becomes unavailable
# https://hub.docker.com/search?q=php54-apache

# Update the sources list since "jessie" (Debian 8) release is archived
COPY ./apt-sources.list /etc/apt/sources.list

COPY ./apache2.conf /etc/apache2/apache2.conf
COPY ./php/php.ini /usr/local/etc/php/php.ini

RUN apt-get update
RUN apt-get -y --force-yes install \
    apt-transport-https \
    apt-utils \
    autoconf \
    bzip2 \
    curl \
    filter \
    gcc \
    ghostscript \
    git \
    gnupg \
    less \
    libc-dev \
    libcurl3 \
    libicu-dev \
    libmcrypt-dev \
    libmysqlclient18 \
    libssh2-1 \
    libxml2 \
    libxslt-dev \
    libzip-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng12-dev \
    make \
    mysql-client \
    pkg-config \
    php-pear \
    php5-dev \
    php5-imagick \
    php5-mcrypt \
    php5-gd \
    php5-ssh2 \
    openssh-client \
    rpm \
    sed \
    vim \
    vsftpd \
    wget 

RUN DEBIAN_FRONTEND=noninteractive apt-get -y --force-yes install openssl

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

# Install PHP extensions
RUN docker-php-ext-install \
    bcmath \
    calendar \
    ctype \
    curl \
    dom \
    exif \
    fileinfo \
    gettext \
    gd \
    hash \
    iconv \
    intl \
    json \
    mbstring \
    mcrypt \
    mysqli \
    pcntl \
    pdo \
    pdo_mysql \
    posix \
    session \
    shmop \
    simplexml \
    soap \
    sockets \
    sysvmsg \
    sysvsem \
    sysvshm \
    tokenizer \
    wddx \
    xml \
    xmlreader \
    xmlrpc \
    xmlwriter \
    xsl \
    zip

RUN docker-php-ext-enable mysqli 

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

# Mailhog
RUN curl -LkSso /usr/bin/mhsendmail 'https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64'&& \
    chmod 0755 /usr/bin/mhsendmail

RUN a2enmod rewrite
RUN a2enmod ssl

WORKDIR /var/www/html

EXPOSE 80
EXPOSE 443

RUN rm -f /usr/local/apache2/logs/httpd.pid
CMD ["apache2ctl", "-DFOREGROUND"]
