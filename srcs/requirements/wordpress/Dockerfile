FROM debian:bullseye

EXPOSE 3306

RUN apt update -y
RUN apt upgrade -y
RUN apt install vim -y
RUN apt install curl -y

RUN apt-get -y install wget
RUN apt-get install -y php7.3\
						php-fpm\
						php-mysql\
						mariadb-client

#RUN wget https://fr.wordpress.org/wordpress-6.5-fr_FR.tar.gz -P /var/www
#RUN cd /var/www && tar -xzf wordpress-6.5-fr_FR.tar.gz && rm wordpress-6.5-fr_FR.tar.gz
#RUN chown -R root:root /var/www/wordpress

COPY /conf/www.conf /etc/php/7.4/fpm/pool.d
RUN chown www-data:www-data /etc/php/7.4/fpm/pool.d/www.conf

#RUN	sed -i "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g" /etc/php/7.4/fpm/php.ini
#RUN sed -i "s/listen = \/run\/php\/php$PHP_VERSION_ENV-fpm.sock/listen = 9000/g" /etc/php/7.4/fpm/pool.d/www.conf
#RUN sed -i "s/;listen.mode = 0660/listen.mode = 0660/g" /etc/php/7.4/fpm/pool.d/www.conf
#RUN sed -i "s/;daemonize = yes/daemonize = no/g" /etc/php/7.4/fpm/pool.d/www.conf

RUN mkdir -p /run/php
RUN mkdir -p /var/run/php/
RUN mkdir -p /var/www/inception/
RUN	chown -R www-data:www-data /var/www/inception/

COPY ./conf/wp-conf.sh /bin
RUN chmod +x /bin/wp-conf.sh
ENTRYPOINT ["/bin/wp-conf.sh"]