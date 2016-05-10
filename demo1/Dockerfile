#Specify which image to use
FROM debian:jessie
MAINTAINER willem@clarin.eu

#Install packages
RUN apt-get update \
 && apt-get install -y nginx

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
 && ln -sf /dev/stderr /var/log/nginx/error.log

#Expose standard http and  https ports
EXPOSE 80 443

#Run nginx in foreground
CMD ["nginx", "-g", "daemon off;"]
