#Specify which image to use
FROM debian:jessie
MAINTAINER willem@clarin.eu

ENV JAVA_HOME /usr 
ENV CATALINA_HOME /usr/share/tomcat8 
ENV CATALINA_BASE /var/lib/tomcat8 
ENV CATALINA_PID /var/run/tomcat8.pid 
ENV JAVA_OPTS "-Djava.security.egd=file:/dev/./urandom"

#Install packages
RUN apt-get update \
 && apt-get install -y \
      supervisor \
      nginx \
      tomcat8

#Copy supervisord configuration
COPY supervisord.conf \
  /etc/supervisor/conf.d/supervisord.conf

#Expose log directories as volumes
VOLUME ["/var/log/nginx", "/var/log/tomcat8"]

#Expose standard http, https and tomcat http #ports
EXPOSE 80 443 8080

#Run supervisord in foreground
CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
