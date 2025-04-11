# This installation is for specific Magento < 1.9 Community Edition
FROM drupalci/php-5.4.45-apache:production

# Update the sources list since "jessie" (Debian 8) release is archived
COPY ./apt-sources.list /etc/apt/sources.list

RUN apt-get purge -y --auto-remove
RUN apt-get clean
RUN apt-get update -y

ENV DEBIAN_FRONTEND="noninteractive"

RUN apt-get -y --force-yes --fix-broken --fix-missing install apt-transport-https
RUN apt-get -y --force-yes --fix-broken --fix-missing install apt-utils
RUN apt-get -y --force-yes --fix-broken --fix-missing install filter
RUN apt-get -y --force-yes --fix-broken --fix-missing install ghostscript
RUN apt-get -y --force-yes --fix-broken --fix-missing install git
RUN apt-get -y --force-yes --fix-broken --fix-missing install less
RUN apt-get -y --force-yes --fix-broken --fix-missing install php-pear
RUN apt-get -y --force-yes --fix-broken --fix-missing install php5-imagick
RUN apt-get -y --force-yes --fix-broken --fix-missing install openssh-client
RUN apt-get -y --force-yes --fix-broken --fix-missing install openssl
RUN apt-get -y --force-yes --fix-broken --fix-missing install rpm
RUN apt-get -y --force-yes --fix-broken --fix-missing install ssh
RUN apt-get -y --force-yes --fix-broken --fix-missing install vim
RUN apt-get -y --force-yes --fix-broken --fix-missing install vsftpd
RUN apt-get -y --force-yes --fix-broken --fix-missing install wget
RUN apt-get -y --force-yes --fix-broken --fix-missing install unzip
RUN apt-get -y --force-yes --fix-broken --fix-missing install zip

# RUN pecl install zendopcache-7.0.3
# RUN echo "zend_extension=/usr/lib/php5/20131226/opcache.so \
#     opcache.memory_consumption=128 \
#     opcache.interned_strings_buffer= 8 \
#     opcache.max_accelerated_files=4000 \
#     opcache.revalidate_freq=60 \
#     opcache.fast_shutdown=1 \
#     opcache.enable_cli=1" > /etc/php5/mods-available/opcache.ini


# # PDFlib
# ENV TNS_ADMIN=/etc
# RUN curl -o /tmp/pdflib-php.tar.gz -SL "http://www.pdflib.com/binaries/PDFlib/906/PDFlib-9.0.6p2-Linux-x86_64-php.tar.gz"
# RUN curl -o /tmp/oracle-instantclient.x86_64.rpm -SL "https://raw.githubusercontent.com/astrobl1904/docker-library/master/php-dev/commercial-components/oracle-instantclient.x86_64.rpm" 
# RUN pecl --setopt=tsflags=nodocs --nogpgcheck -y install tar /tmp/oracle-instantclient.x86_64.rpm 
# RUN install -m 755 -d /usr/lib64/php/modules 
# RUN tar -xzf /tmp/pdflib-php.tar.gz -C /usr/lib64/php/modules --no-same-owner --no-same-permissions --wildcards --strip-components=4 */php-700/php_pdflib.so 
# RUN echo "/usr/lib/oracle/12.1/client64/lib" > /etc/ld.so.conf.d/oracle-instantclient.x86_64.conf 
# RUN echo "# Placeholder tnsnames.ora for Docker containers" > $TNS_ADMIN/tnsnames.ora 
# RUN rm -rf /tmp/*.rpm /tmp/*.tar.gz
# RUN echo "extension=php_pdflib.so" > /etc/php5/mods-available/pdflib.ini

# # Mailhog
RUN curl -LkSso /usr/bin/mhsendmail 'https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64'&& \
    chmod 0755 /usr/bin/mhsendmail

# COPY ./apache2/apache2.conf /etc/apache2/apache2.conf
# COPY ./apache2/php.ini /etc/php5/apache2/php.ini
# RUN cp /etc/php5/apache2/php.ini /usr/local/etc/php/php.ini

# # Install PHP extensions
RUN docker-php-ext-install    bcmath 
RUN docker-php-ext-install    calendar 
RUN docker-php-ext-install    ctype 
RUN docker-php-ext-install    curl 
RUN docker-php-ext-install    dom 
RUN docker-php-ext-install    exif 
RUN docker-php-ext-install    fileinfo 
RUN docker-php-ext-install    gettext 
RUN docker-php-ext-install    hash 
RUN docker-php-ext-install    iconv 
RUN docker-php-ext-install    intl 
RUN docker-php-ext-install    json 
RUN docker-php-ext-install    mbstring 
RUN docker-php-ext-install    mcrypt 
RUN docker-php-ext-install    mysqli 
RUN docker-php-ext-install    pcntl 
RUN docker-php-ext-install    pdo 
RUN docker-php-ext-install    pdo_mysql 
RUN docker-php-ext-install    posix 
RUN docker-php-ext-install    session 
RUN docker-php-ext-install    shmop 
RUN docker-php-ext-install    simplexml 
RUN docker-php-ext-install    soap 
RUN docker-php-ext-install    sockets 
RUN docker-php-ext-install    sysvmsg 
RUN docker-php-ext-install    sysvsem 
RUN docker-php-ext-install    sysvshm 
RUN docker-php-ext-install    tokenizer 
RUN docker-php-ext-install    wddx 
RUN docker-php-ext-install    xml 
RUN docker-php-ext-install    xmlreader 
RUN docker-php-ext-install    xmlrpc 
RUN docker-php-ext-install    xmlwriter 
RUN docker-php-ext-install    xsl 
RUN docker-php-ext-install    zip

# RUN cp /usr/lib/php5/20131226/* /usr/local/lib/php/extensions/no-debug-non-zts-20100525/
# RUN cp /usr/lib64/php/modules/php_pdflib.so /usr/local/lib/php/extensions/no-debug-non-zts-20100525/
RUN ln -s /etc/php5/mods-available/* /usr/local/etc/php/conf.d/

RUN a2enmod ssl
RUN service apache2 restart

WORKDIR /var/www/html

EXPOSE 80
EXPOSE 443

RUN rm -f /usr/local/apache2/logs/httpd.pid
CMD ["apache2ctl", "-DFOREGROUND"]
