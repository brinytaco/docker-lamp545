# Docker LAMP PHP 5.4.45
This Docker image is based on the `php:5.4-apache` image. It has been tailored
specifically for a Magento 1.6 Community Edition installation.

### **Linux:** Debian GNU/Linux 8 (jessie)<br>
### **Apache:** 2.4.10 (Debian)<br>
### **MYSQL:** Maria DB 10.7.1<br>
### **PHP:** 5.4.45<br>
#### PHP Included Extensions:<br>
(To add additional extensions, add the desired entries/commands to the ./build/php/Dockerfile)

    bcmath bz2 calendar Core ctype curl date dom ereg exif fileinfo filter gd gettext hash iconv imagick intl json libxml mbstring
    mysqli mysqlnd openssl pcntl pcre PDO pdo_mysql pdo_sqlite Phar posix readline recode Reflection session shmop SimpleXML soap
    sockets SPL sqlite3 standard sysvmsg sysvsem sysvshm tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zip zlib

This Docker image also includes the following component images:

### **Mailhog:** (Latest)
MailHog is an email testing tool for developers:
- Configure your application to use MailHog for SMTP delivery
- View messages in the web UI, or retrieve them with the JSON API
- Optionally release messages to real SMTP servers for delivery
- See https://github.com/mailhog/MailHog

### **phpMyAdmin:**  (Latest)
