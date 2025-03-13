FROM debian:bullseye

RUN apt update -y
RUN apt upgrade -y
RUN apt install vim -y
RUN apt install curl -y
RUN apt-get install mariadb-server -y

RUN mkdir -p /run/mysqld/
RUN chown mysql:mysql /run/mysqld
RUN chmod 755 /run/mysqld

COPY conf/50-server.cnf	/etc/mysql/mariadb.conf.d/
COPY ./tools/mariadb-setup.sh /var/local/bin/mariadb-setup.sh
RUN chmod +x /var/local/bin/mariadb-setup.sh
#CMD /usr/bin/mysqld_safe

#CMD ["mysqld_safe"]
ENTRYPOINT ["/var/local/bin/mariadb-setup.sh"]