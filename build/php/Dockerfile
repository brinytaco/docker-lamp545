FROM php:5.4-apache

# COPY ./php.ini /usr/local/etc/php/php.ini

# update package list
RUN apt-get update

RUN apt-get -y --force-yes install git
RUN apt-get -y --force-yes install curl
RUN apt-get -y --force-yes install vim
RUN apt-get -y --force-yes install apt-utils
RUN apt-get -y --force-yes install libxml2-dev
RUN apt-get -y --force-yes install gnupg
RUN apt-get -y --force-yes install apt-transport-https
RUN apt-get -y --force-yes install libicu-dev

RUN apt-get -y --force-yes install mcrypt
RUN apt-get -y --force-yes install php-pear 
