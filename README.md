# Docker image of Wordpress with LDAP support
This images is based on the "wordpress:php8.2-apache" tag

Just added this code snippet as suggested by https://github.com/tianon, Wordpress official image mantainer:

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
  
  To build the images just run:
  
  ````
  docker build -t [username]/[imagename] .
  ````
