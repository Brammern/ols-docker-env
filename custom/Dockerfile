FROM litespeedtech/openlitespeed:1.8.3-lsphp83

# Set variables
ENV PHP_VERSION=8.3 \
    PHP_API=20220829 \
    LSPHP_VERSION=lsphp83

# Install ionCube directly into PHP extensions dir
RUN curl -sSL https://downloads.ioncube.com/loader_downloads/ioncube_loaders_lin_x86-64.tar.gz \
    | tar -xz -C /tmp && \
    cp /tmp/ioncube/ioncube_loader_lin_${PHP_VERSION}.so \
       /usr/local/lsws/${LSPHP_VERSION}/lib/php/${PHP_API}/ioncube_loader_lin_${PHP_VERSION}.so && \
    rm -rf /tmp/ioncube*

# Inject ionCube loader into php.ini & Disable the prebuilt OPcache.
RUN echo "zend_extension=/usr/local/lsws/${LSPHP_VERSION}/lib/php/${PHP_API}/ioncube_loader_lin_${PHP_VERSION}.so" \
    >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini && \
    echo "opcache.enable=0" >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini && \
    echo "opcache.enable_cli=0" >> /usr/local/lsws/${LSPHP_VERSION}/etc/php/${PHP_VERSION}/litespeed/php.ini
