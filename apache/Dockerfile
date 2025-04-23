FROM httpd:2.4

RUN apt-get update && apt-get install -y libapache2-mod-fcgid curl \
    && apt-get clean

COPY conf/my-vhost.conf /usr/local/apache2/conf/extra/my-vhost.conf

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN echo "Include conf/extra/my-vhost.conf" >> /usr/local/apache2/conf/httpd.conf
RUN a2enmod proxy proxy_fcgi rewrite
