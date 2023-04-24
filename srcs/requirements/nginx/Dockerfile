FROM debian:buster

RUN apt update
RUN apt install nginx -y
RUN apt install vim -y
RUN apt install curl -y
RUN mkdir -p /etc/nginx/ssl
RUN apt install openssl -y
#RUN openssl req -x509 -nodes -out /etc/ssl/certs/inception.crt -keyout /etc/ssl/private/inception.key -subj "/C=FR/ST=IDF/L=Paris/O=42/OU=42/CN=jroux-fo.42.fr/UID=jroux-fo"

RUN openssl req \
	-newkey rsa:4096 -nodes \
	-keyout /etc/ssl/private/inception.key \
	-x509 -days 365 \
	-out /etc/ssl/certs/inception.crt \
	-subj "/C=FR/ST=IDEF/L=Paris/O=42/OU=42/CN=jroux-fo.42.fr/UID=jroux-fo"

RUN mkdir -p /var/run/nginx
COPY conf/nginx.conf /etc/nginx/nginx.conf
RUN chmod 755 /var/www/html
RUN chown -R www-data:www-data /var/www/html

CMD ["nginx", "-g", "daemon off;"]
