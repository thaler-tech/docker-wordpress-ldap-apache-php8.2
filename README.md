# Docker image of WordPress with LDAP support
This image is based on the "wordpress:php8.2-apache" tag

This is forked from dalario's wordpress-ldap Docker hub which in turn was suggested from https://github.com/tianon:

````
FROM wordpress:php8.2-apache

RUN set -x \
	&& apt-get update \
	&& apt-get install -y libldap2-dev \
	&& rm -rf /var/lib/apt/lists/* \
	&& docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ \
	&& docker-php-ext-install ldap \
	&& apt-get purge -y --auto-remove libldap2-dev
  ````
  
  To build the image just run:
  
  ````
  docker build -t [username]/[imagename] .
