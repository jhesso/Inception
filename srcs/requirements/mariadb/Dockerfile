FROM	alpine:3.18

# Install MariaDB
RUN		apk update && apk upgrade &&\
		apk add mariadb mariadb-client

# Copy MariaDB config file
COPY	./conf/configure.sh /tmp/configure.sh
Run		chmod +x /tmp/configure.sh

# Run MariaDB config script
ENTRYPOINT	["sh", "/tmp/configure.sh"]
