FROM	debian

#install nginx
RUN	apt-get update
RUN	apt-get install -y nginx openssl

#nginx SSL
RUN	mkdir /etc/nginx/ssl
RUN	openssl req -newkey rsa:4096 -x509 -sha256 -days 365 -nodes \
	-out /etc/nginx/ssl/jhesso.crt \
	-keyout /etc/nginx/ssl/jhesso.key \
	-subj "/C=FR/ST=Paris/L=Paris/O=42 School/OU=jhesso/CN=jhesso/"

# nginx config
COPY	./conf/nginx.conf /etc/nginx/conf.d
RUN	mkdir -p /run/nginx

# Open the only allowed port
EXPOSE	443

# Start nginx
CMD	["nginx", "-g", "daemon off;"j
