# Docker LAMP PHP 5.4.45
This Docker image [`brinytaco/linux-php54:magento`](https://hub.docker.com/r/brinytaco/linux-php54) is based on the [`drupalci/php-5.4.45-apache:production`](https://hub.docker.com/r/drupalci/php-5.4.45-apache) image. 
It has been tailored specifically for a Magento 1.6 Community Edition installation with all necessary modules and php extensions.

## **Linux:** Debian GNU/Linux 8 (jessie) ##
## **PHP:** 5.4.45 ##
## **Apache:** 2.4.10 (Debian) ##
## **MYSQL:** MySQL Ver 14.14 Distrib 5.5.62 ##
## Installed Modules
    apt-transport-https apt-utils autoconf bzip2 curl filter gcc ghostscript git gnupg less libc-dev libcurl3 libicu-dev libmcrypt-dev libmysqlclient18 libssh2-1 libxml2 libxslt-dev libzip-dev libfreetype6-dev libjpeg62-turbo-dev libpng12-dev make mysql-client openssh-client pkg-config php-pear php5-ssh2 php5-dev php5-imagick php5-mcrypt php5-gd rpm sedvim vsftpd wget

### **PHP Included Extensions:** ###
    bcmath calendar ctype curl dom exif fileinfo gettext gd hash iconv intl json mbstring mcrypt mysqli pcntl pdo pdo_mysql posix session shmop simplexml soap sockets ssh2 sysvmsg sysvsem sysvshm tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip

#### This Docker image also includes the following component images: ####

### **PDFlib** (9.0.6) ###

### **Mailhog:** (Latest)
MailHog is an email testing tool for developers:
- Configure your application to use MailHog for SMTP delivery
- View messages in the web UI, or retrieve them with the JSON API
- Optionally release messages to real SMTP servers for delivery
- See https://github.com/mailhog/MailHog

### **phpMyAdmin:**  (Latest)
