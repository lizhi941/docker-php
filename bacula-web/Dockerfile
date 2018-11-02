# php:7.2-apache From docker hub offical images 

FROM php:7.2-apache    

LABEL "Maitainer.name"="Zhi Li"
LABEL "Maitainer.email"="lizhi941@sohu.com"

# To install php-extensions (gd ,gettext ,pgsql ,mysql)
# they are nessisary for running bacul-web 
RUN requirements="libfreetype6-dev libjpeg62-turbo-dev libpng-dev postgresql-server-dev-all" \
    && apt-get update \
    && apt-get install -y $requirements \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pgsql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install gettext  \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && requirementsToRemove="" \
    && apt-get purge --auto-remove -y $requirementsToRemove

#you can get sourcecode from website http://www.bacula-web.org
ADD bacula-web-8.0.1.tgz /var/www/html/   

# because apache create a user www-data,so need to change the owner
RUN chown -R www-data /var/www/html/      
ADD run.sh /run.sh
RUN chmod +x /run.sh
CMD /run.sh
