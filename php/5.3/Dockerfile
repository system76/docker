FROM php:5.3-apache

RUN curl https://ftp-master.debian.org/keys/archive-key-8.asc | apt-key add -

COPY sources.list /etc/apt/sources.list
COPY 10check-valid-until /etc/apt/apt.conf.d/10check-valid-until
