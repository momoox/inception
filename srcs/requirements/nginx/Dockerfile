FROM debian:bullseye

RUN apt update
RUN apt upgrade
RUN apt install nginx -y
RUN apt install vim -y    
RUN apt install curl -y
#folder to store certificat and key ssl
RUN mkdir -p /etc/nginx/ssl
#tool to manage and create certificats for ssl
RUN apt install openssl -y
#create ssl certificate
RUN openssl req -x509 -nodes -out /etc/nginx/ssl/inception.crt -keyout /etc/nginx/ssl/inception.key -subj "/C=FR/ST=IDF/L=Mulhouse/O=42/OU=42/CN=mgeisler.42.fr/UID=mgeisler"
#folder to store nginx files
RUN mkdir -p /var/run/nginx
#copy config lines into folder and file nginx
COPY conf/nginx.conf /etc/nginx/nginx.conf
#root principal
RUN chmod 755 /var/www/html
#principal user
RUN chown -R www-data:www-data /var/www/html
RUN touch /tmp/started
#launch nginx in "premier plan" so the container doesn't stop
CMD [ "nginx", "-g", "daemon off;" ]