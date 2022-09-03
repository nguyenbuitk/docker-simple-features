# BASE
FROM alpine
# RUN

RUN apk add nginx; \
    apk add dos2unix; \
    echo "<h1>Hello world!</h1>" > /var/www/localhost/htdocs/index.html

# RUN ["/bin/sh", "-c", "apk add nginx; apk add dos2unitx; echo  "<h1>Hello world!</h1>" > /var/www/localhost/htdocs/index.html"]
# CONFIGUTATIONS
# nginx configuration

ADD $PWD/config/default.conf /etc/nginx/http.d/default.conf
# keys and certs
ADD $PWD/config/nginx-dockerfile.key /etc/ssl/private/nginx-dockerfile.key
ADD $PWD/config/nginx-dockerfile.crt /etc/ssl/certs/nginx-dockerfile.crt
WORKDIR /var/www/localhost/htdocs
# ENTRYPOINT

COPY $PWD/config/entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint.sh

WORKDIR /etc/nginx/http.d

#CMD ["/bin/sh", "-c", "nginx -g 'daemon off;'; nginx -s reload;"]
# # EXPOSE PORTS
EXPOSE 80
EXPOSE 443
# RUN COMMAND