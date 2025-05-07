FROM litespeedtech/openlitespeed:1.8.3-lsphp82

# Set variables
ENV PHP_VERSION=8.2 \
    PHP_API=20220829 

# Install ionCube directly into PHP extensions dir
RUN curl -sSL https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
    | tar -xz -C /tmp && \
    cp /tmp/ioncube/ioncube_loader_lin_${PHP_VERSION}.so \
       /usr/local/lsws/lsphp82/lib/php/${PHP_API}/ioncube_loader_lin_${PHP_VERSION}.so && \
    rm -rf /tmp/ioncube*

# Disable OPcache by removing the file
RUN rm -f /usr/local/lsws/lsphp82/etc/php/{PHP_VERSION}/mods-available/opcache.ini

# Inject ionCube loader into php.ini
RUN echo "zend_extension=/usr/local/lsws/lsphp82/lib/php/${PHP_API}/ioncube_loader_lin_${PHP_VERSION}.so" \
    >> /usr/local/lsws/lsphp82/etc/php/${PHP_VERSION}/litespeed/php.ini
