FROM	alpine:3.18

# install nginx and ssl
RUN		apk update && apk upgrade &&\
		apk add nginx openssl

# nginx SSL
RUN	openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout /etc/ssl/private/nginx-selfsigned.key \
	-out /etc/ssl/certs/nginx-selfsigned.crt \
	-subj "/C=FR/ST=Paris/L=Paris/O=42 School/OU=jhesso/CN=jhesso/"

# nginx config
COPY	./conf/nginx.conf /etc/nginx/nginx.conf
COPY	./conf/default.conf /etc/nginx/http.d/default.conf
RUN		mkdir -p /var/www/html/

RUN		adduser -D -g 'www' www &&\
		chown -R www:www /run/nginx/ &&\
		chown -R www:www /var/www/html/

# Open the only allowed port
EXPOSE	443/tcp

# Start nginx
ENTRYPOINT	["nginx"]
CMD			["-g", "daemon off;"]
