FROM ubuntu:latest
MAINTAINER Alex Callard "alex@wearenotmachines.com"
RUN apt-get install -y language-pack-en-base
RUN locale-gen en_GB.UTF-8
RUN export LANG=en_GB.UTF-8
RUN export LC_ALL=en_GB.UTF-8
RUN apt-get update
RUN apt-get install -y apache2 curl wget nano software-properties-common openssh-server
RUN mkdir -p /var/log/supervisor
RUN a2enmod rewrite

#RUN echo '[supervisord]' >>  /etc/supervisor/conf.d/supervisord.conf
#RUN echo 'nodaemon=true' >> /etc/supervisor/conf.d/supervisord.conf
#RUN echo '[program:apache2]' >> /etc/supervisor/conf.d/supervisord.conf
#RUN echo 'command=/bin/bash -c "source /etc/apache2/envvars && exec /usr/sbin/apache2 -DFOREGROUND"' >>


RUN LC_ALL=en_GB.UTF-8 apt-add-repository ppa:ondrej/php-7.0
RUN apt-get update
RUN apt-get install -y php7.0
RUN echo '<?php phpinfo(); ?>' > /var/www/html/index.php
RUN rm /var/www/html/index.html
RUN echo service apache2 start >> /etc/bash.bashrc
RUN sed -i.orig 's/#ServerName/ServerName/' /etc/apache2/apache2.conf
EXPOSE 80
CMD ["/usr/sbin/apachectl", "-D FOREGROUND"]
