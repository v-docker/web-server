#
# Nginx Dockerfile
# v-docker/web-server
#
#

# Pull base image.
FROM ubuntu:16.04

# Install Nginx.
RUN \
  apt-get update && \
  apt-get install -y nginx && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx

# Install PHP-FPM.
RUN \
  apt-get install php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-mcrypt php-ldap php-zip php-curl -y

RUN rm -rf /var/lib/apt/lists/*

# Define mountable directories.
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Define working directory.
WORKDIR /etc/nginx

CMD ["/bin/bash", "-c", "/usr/sbin/service php7.0-fpm start && nginx"]
# Expose ports.
EXPOSE 80
EXPOSE 443
