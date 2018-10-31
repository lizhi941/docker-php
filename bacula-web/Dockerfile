FROM php:7.2-apache

ADD bacula-web-8.0.1.tgz /var/www/html/

RUN chown -R www-data /var/www/html/ && \
    chmod -R u=rx,g=rx,o=rx /var/www/html/ && \
    chmod -R u=rwx,g=rwx,o=rx /var/www/html/application/views/cache

ADD run.sh /run.sh
RUN chmod +x /run.sh
CMD /run.sh
