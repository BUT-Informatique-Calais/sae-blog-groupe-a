FROM httpd:2.4

RUN apt-get update && apt-get install -y libapache2-mod-fcgid curl \
    && apt-get clean

RUN sed -i \
    -e 's/^#\(LoadModule proxy_module modules\/mod_proxy.so\)/\1/' \
    -e 's/^#\(LoadModule proxy_fcgi_module modules\/mod_proxy_fcgi.so\)/\1/' \
    /usr/local/apache2/conf/httpd.conf

COPY conf/my-vhost.conf /usr/local/apache2/conf/extra/my-vhost.conf
RUN sed -i \
    -e 's/#Include\ conf\/extra\/httpd-vhosts.conf/Include\ conf\/extra\/my-vhost.conf/' \
    /usr/local/apache2/conf/httpd.conf

WORKDIR /var/www/html

EXPOSE 80

CMD ["httpd-foreground"]