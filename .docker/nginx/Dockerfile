FROM nginx:latest

ADD nginx.conf /etc/nginx/conf.d/default.conf

RUN mkdir /var/www

RUN chown -R www-data:www-data /var/www

WORKDIR /var/www

#EXPOSE <PORT_NUMBER>

# CMD ["nginx", "-g", "daemon off;"]